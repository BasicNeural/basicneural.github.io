---
title: 하스켈로 푸리에 변환 시각화하기
subtitle: OpenGL로 그려봄
categories: 개발
tags: [Haskell, OpenGL, 수학]
comments: true
---
3Blue1Brown의 [푸리에 변환이 대체 뭘까요?](https://youtu.be/spUNpyF58BY) 라는 영상을 보고 삘받아서 만들어봤다.

![](/post-img/fourier-series-1.gif)

푸리에 적분 그래프는 직접 적분한거 그린게 아니라 그래프 보고 그래프 점들 모와서 평균낸거라 완벽하지는 않다.
그래도 그래프 꽤 이쁘게 잘 나왔다!

파형 그래프는 아래의 공식과 같다.
```haskell
g t = (sin t + sin (2*t)) / 2
```