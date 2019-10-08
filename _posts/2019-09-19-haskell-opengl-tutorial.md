---
layout: post
title: 하스켈로 OpenGL 하기
subtitle: FreeGLUT로 간단하게 만들어봅시다
tags: [개발, Haskell, OpenGL]
comments: true
---


## 이 게시글은 [OpenGLTutorial](https://wiki.haskell.org/OpenGLTutorial1)을 참고하여 작성되었습니다.

하스켈도 OpenGL을 써서 그래픽 구현을 할 수 있는데 한국어로는 자료가 없는 것 같아 써봅니다.

이번에 할 것은 GLUT로 실시간 그래프를 그리는 것을 해 보도록 하겠습니다.

```haskell
import Graphics.UI.GLUT
 
main :: IO ()
main = do
  (_progName, _args) <- getArgsAndInitialize
  _window <- createWindow "Hello World"
  displayCallback $= display
  mainLoop
 
display :: IO ()
display = do
  clear [ ColorBuffer ]
  flush
```
위의 코드가 가장 기본적인 GLUT 코드인데, `createWindow` 로 윈도우를 생성하고, `displayCallback` 으로 화면을 그리는 콜백을 등록한 후, 프로그램을 실행하게 됩니다.
콜백의 종류는 `idleCallback`, `reshapeCallback` 등이 있으며 [GLUT 패키지](http://hackage.haskell.org/package/GLUT-2.7.0.15/docs/Graphics-UI-GLUT-Callbacks.html)를 통해 알 수 있습니다.

실시간으로 그리기 위해서는 프로그램이 돌아가는 동안 게속 반복되는 동작이 필요한데, 이 동작을 위해 `idleCallback` 과 `addTimerCallback` 이 있습니다.
`idleCallback` 은 콜백으로 등록한 함수가 종료되면 바로 다시 호출하는 함수이고, `addTimerCallback` 은 함수를 실행하고, 등록한 시간 후에 다시 실행 하는 함수힙니다. 저는 `idleCallback` 을 기준으로 설명하겠습니다.

```haskell
import Graphics.UI.GLUT
 
main :: IO ()
main = do
  (_progName, _args) <- getArgsAndInitialize
  _window <- createWindow "Hello World"
  displayCallback $= display
  idleCallback $= Just idle
  mainLoop

...

idle :: IO ()
idle = return ()
```

위의 코드처럼 하면 프로그램 실행 후, 프로그램이 종료될 순간 까지 idle 함수를 반복적으로 호출하게 됩니다.
하지만 아무것도 못하는 함수를 그냥 실행하기만 해서는 우리가 원하는 결과물을 가져올 수 없습니다.

## IORef

하스켈은 기본적으로 변수가 존재하지 않기 때문에 함수별로 변수를 공유하기 위해서는 다른 방법을 써야 합니다. 저는 `IORef` 사용하는 방법으로 설명하겠습니다.

`IORef` 는 하스켈에서 변수를 사용 할 수 있는 방법중 하나로써, 이름처럼 IO 모나드에서 사용 할 수 있는 자료형입니다.
우리가 사용할 함수는 `newIORef`, `readIORef`, `modifyIORef`, 총 세가지 입니다.
* `newIORef` 는 IORef 변수를 만드는 함수로써 인자로 초기화 할 값을 받습니다.
* `readIORef` 는 변수에서 값을 추출하는 함수로써 `IORef a` 타입 인자를 받습니다.
* `modifyIORef` 는 변수의 값을 바꾸는 함수로써 `a -> a` 타입 함수를 받습니다.

이 함수를 이용하여 `IORef` 를 만들고, `idle` 함수와 `display` 함수의 인자로 만들어 주면, 서로간의 값을 공유 할 수 있게 됩니다.

```haskell
import Graphics.UI.GLUT
import Data.IORef
 
main :: IO ()
main = do
  (_progName, _args) <- getArgsAndInitialize
  _window <- createWindow "Hello World"

  foo <- newIORef (0.0 :: Float)

  displayCallback $= display foo
  idleCallback $= Just (idle foo)
  mainLoop

display :: IORef Float -> IO ()
display fooRef = do
  clear [ ColorBuffer ]
  foo <- readIORef fooRef

  renderPrimitive Points $
    vertex $ Vertex2 0 (sin foo)
  flush

idle :: IORef Float -> IO ()
idle fooRef = do
  modifyIORef fooRef (+0.01)
  postRedisplay Nothing
```

위와 같은 코드를 작성하면 아래의 결과를 얻을 수 있습니다.

![](/post-img/glut-example-1.gif)