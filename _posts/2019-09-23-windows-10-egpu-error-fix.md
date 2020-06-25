---
title: 윈도우 10 egpu 에러 해결
categories: 기타
comments: true
---
어느날 윈도우를 사용하는데 egpu 연결 시 `리소스 부족 12` 에러가 났다.
최근의 변경사항을 생각해봤더니, 윈도우 업데이트가 문제였던것 같다.
그래서 윈도우 업데이트를 하나씩 지워 보면서 문제가 되는 업데이트를 찾았다.
문제가 되는 업데이트는 `KB4515384` 업데이트였다.
업데이트 제거만으로는 나중에 다시 업데이트가 될 수 있기 때문에 업데이트 자체를 숨겨야 했다.
검색을 하던 도중 
[Windows 10에서 Windows 업데이트가 임시로 다시 설치되지 않도록 하는 방법](https://support.microsoft.com/ko-kr/help/3183922/how-to-temporarily-prevent-a-windows-update-from-reinstalling-in-windo)
 을 찾게 되었다.
이 프로그램을 실행하면 아래의 사진처럼 업데이트를 숨길 수 있다.
![](/post-img/windows-update-hide.png)

나와 비슷한 상황의 문제를 가진 사람을 위해 PC의 사양을 적어본다.

* Macbook pro 2018 13"
* Razer core v1
* Radeon vega 56
* Windows 10 1903 

## 내용 추가

이러한 문제는 최신 버전의 pci 드라이버가 Radeon 그래픽카드가 egpu 환경에서 호환이 되지 않는 문제이다. 구버전 윈도우에서 `pci.sys`파일을 추출해서 현재 윈도우의 파일을 교환하면 해결 할 수 있다. 일부 업데이트는 `pci.sys` 파일을 교체하기 때문에 업데이트 후 egpu 실행이 불가능하다면 다시 교체해야 한다.