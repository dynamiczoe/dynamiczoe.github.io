---
layout: post
title:  "Jekyll 블로그에 포스트가 업데이트 되질 않는다! 근데, 그렇다면 이 글은 어떻게 썼지?!"
date:   2016-02-21
author: 박정환
categories: DevOps
tags:	DevOps 
cover:  "/assets/Earth.png"
---

Jekyll 에는 `Future`라는 속성이 있다.
이 속성은 글을 올리는 시각이 미래로 되어있을경우 블로그상에 글을 나타낼 것인지 판단하는 기준이되는 속성이다.

이번 github 블로그에 jekyll 3.0 패지가 되었다.
이번 패치에서 여러 변경이 있었는데, 그중 Future 속성 기본값이 false로 setting 되었다고 한다.

나는 글을 올릴때 시, 분까지 기입하는데, UTC보다 9시간 빠른 우리나라의 시간을 적어 넣으니 **당연히 안올라갔던것.**

빌드가 제대로 이루어지지않은건지 이것저것 찾아보다가 두시간만에 공식 Document를 읽고 이유를 알아냈다.

그뒤론 9시간 뺀 UTC를 적어야겠다는 생각을 했다.

### 또, Official Document를 먼저 읽는 것을 습관화 해야 겠다고 마음먹었다.
