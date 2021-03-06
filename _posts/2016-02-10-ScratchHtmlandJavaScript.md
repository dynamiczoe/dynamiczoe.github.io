---
layout: post
title:  "Scratch, HTML and Javascript"
date:   2016-02-10 12:37:11
author: 박정환
categories: DevOps
tags:	DevOps
cover:  "/assets/Earth.png"
---
# HTML은

한 화면에는 각각 한쌍의 head, body 로 이루어져있다. 
(우리는 include 하는 문서에도 head와 body문이 포함되어 중첩이 되었었다.)

head에는 문서의 제목등을 나타내는 속성만 들어있어야 한다.

렌더링되고, 기능을 지닌 내용들은 body문 내부에 속해야 한다.

또한 cdn을 사용하여 js나 css 파일을 웹에서 받아 사용한다면, 
브라우저는 그 파일들을 위에서 아래로 순차적으로 one by one 다운로드 받을 것이다.
때문에, 다운받는 파일이 많다면 그 크기들 만큼 오래 걸릴 것이다.

과거에는 인터넷 속도가 빠르지 않아, body문 초입에 그런 문서들을 링크해논 경우, 사이트의 외형이 그려지는데 시간이 오래걸리는 사이트가 많았다.
다시한번 생각해보면 js파일은 기능적인 구현을 가진 경우가 많은데, 기능을 담당하는 문장의 경우 body문 가장 끝에 포함시키는 것이 과거부터 관례가 되었다.
하지만 요즘의 인터넷에서는 상관 없는 일이지만, 그러한 규칙들이 문서를 읽기 쉽게 해준다.


# CSS는
같은 아이디나 클래스에 여러종류의 스타일 속성이 정의 되는 경우 cascade 한 속성을 가지고 있어, 가장 마지막의 속성이 override 해 버린다.
따라서 여러번 중첩하여 적용된 style이 있다면, 렌더링에 문제를 초래할 수 있다.

css를 inline으로 style 지정한 명령이 가장 상위의 명령으로 인식된다.
따라서 css파일에서 정의해 놓았지만, html 문서에서 해당 엘리먼트에 inline style로 주면 override 된다.

inline 정의가 편할 경우도 있지만 유지보수시 엘리먼트를 찾기도 힘들고,
많이 선언되어 있는경우 일일히 변경시켜줘야하는 일이 발생한다.
css파일로 독립시키는 것이 일반적이고 비용이 적게 든다.

# Java Script는
해당 엘리먼트에서 inline event listener를 선언한 경우, 해당 함수가 document에서 호출되는 위치보다 먼저 선언 되어 있어야 한다.
하지만 이는 html문서의 가독성을 낮추고, 유지보수시에도 불편하다.
따라서 jquery selector를 사용하여 엘리먼트를 찾고, 그엘리먼트에 리스너를 붙여주는 방법을 쓴다.
그런 방법을 사용하면 body 말미에 js를 import해도 문제가 발생하지 않으며, 유지보수시에도 간편하다.

---
        위 내용들을아직은 우리의 서비스에 적용해보지 않았지만.(일부 적용 해 보았다. head, body중첩 빼기등)
        Java Script에 대해서는 앞으로 많은 공부를 해야할거라고 생각이 들었다.
        특히 클래스와 객체를 이용한 프로그래밍을 할 수 있다는 우윤정 책임님의 말씀을 듣고 흥미가 많이 생겼다.
