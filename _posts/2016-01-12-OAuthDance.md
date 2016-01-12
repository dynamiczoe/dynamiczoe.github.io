---
layout: post
title:  "OAuth Dance"
date:   2016-01-12 21:38:06
author: 박정환
categories: DevOps
tags:	DevOps OAuth 
cover:  "/assets/Earth.png"
---
# OAuth의 탄생

OAuth 는 인증을 위한 오픈 스탠더드 프로토콜이다.
사용자는 Facebook 이나 Twitter 같은 인터넷 서비스의 기능을 다른 애플리케이션에서도 사용할 수 있게 한다.

# OAuth의 이해

OAuth는 인증뿐만 아니라 허가또한 포함하고 있다.
사용자를 인증하고, 제3자가 어떤 정보나 서비스에 사용자의 권한으로 접근함을 허락한다.

# OAuth와 OpenID의 차이

둘다 인증을 위한 표준 프로토콜이며 HTTP를 사용하나, 목적은 엄연히 다르다.

OpenID의 주목적은 인증이고, OAuth의 주목적은 허가이다.

그로인해 OpenID를 사용한것은 로그인하는 행동과 같다. 이를 사용하는 여러 서비스들은 OpenID Provider에게 인증을 위임 하기 때문이다.

물론 OAuth에도 인증 과정이 있다. 각 Service Provider는 자신의 사용자인지 인증하는 절차를 거친다. 하지만 주목적은 해당 Service에 글을 쓸수있는 api 권한이나, 친구목록을 가져오는 api를 호출 할 권한이 있는 사용자 인지 확인하는 것이다.

# OAuth Dance

OAuth 1.0의 인증 과정을 OAuth Dance라고 한다.
마치 두명이 춤추듯 정확하게 정보를 주고 받는 과정처럼 보여서 라고 한다.

인증과정을 이해하기 위해서는 몇가지 용어를 알아두어야 한다.

> User : Service Provider에 계정을 가지고 있고 Consumer를 이용하려는 사용자.
Service Provider : OAuth를 사용하는 Open API 를 제공하는 서비스.
Cousumer : OAuth인증을 사용해 Service Provider의 기능을 사용하려는 애플리케이션이나 서비스.
Request Tokken : Consumer가 Service Provider 에게 접근 권한을 인증받기 위해 사용하는 값. 인증이 완료된후에는 Access Tokken으로 교환한다.
Access Tokken : 인증후 Consumer가 Service Provider의 자원에 접근하기위한 키를 포함한 값.

# 순서

1. Consumer는 Service Provider 에게 `Request Tokken 을 요청`한다.
2. Service Provider는 `Request Tokken을 반환`해줍니다. 이를받은 Consumer는 `oauth_signature를 생성`합니다.
3. Consumer가 Service Provider로부터 `인증 페이지를 호출`합니다. User는 Service 계정 인증을 합니다.
4. 인증을 마치면 Service Provider가 새로운 `oauth_tokken` 과 `verifier` 를 `Consumer 에게 전달`합니다.
5. Consumer는 oauth_tokken 과 verifier로 Service Provider에게 `Access Tokken을 요청`합니다.
6. Service Provider는 `Access Tokken`을 Consumer 에게 전달한다.
7. Consumer는 Access Tokken을 이용해 `Open API를 요청`한다.
> 이때, HTTP POST가 아닌 `HEAD 방식`을 이용하며, ServiceProvider 에 따라 `realm` 이라는 매개변수를 사용해야 할 경우가 있다. 이는 optional 매개변수인데, WWW-Authentication HTTP 헤더필드에서 사용하는 값이다.

