---
layout: post
title:  "자바 개발환경 설치"
date:   2023-05-14 13:00
categories: Java
thumbnail: /assets/img/posts/java.png
tags: 객체지향
comments: 1
---

<h5> JDK(Java Development Kit  </h5>
- JDK라는 프로그램을 다운로드하고 설치해야한다.
- JDK는 여러 JDK가 존재하는데 (OpenJDK, Oracle JDK, Azul Julu JDK, Amazon Corretto, Adoptium Temurin...) 과거에 일반적으로 Oracle JDK를 주로 사용했으며, JDK간에 호환이 다되기 때문에 어떤 JDK를 설치해도 무방하다. 
- 일반적으로 기업에서 JDK8과 JDK11을 사용하는데 초보자가 공부할 때 사용할 경우 JDK8로도 충분하다.

<h5> Git  </h5>
- Git 설치후 다음의 내용을 설정하는것을 권장한다. (운영체제 마다 명령어가 다를 수 있으니 검색해보고 하는것을 추천)
	1. git config --global user.name "이름"
	2. git config --global user.email 이메일
	3. git config --global core.autocrlf true
		- 운영체제 마다 줄바꿈과같은 특정 문자의 변환 코드가 다르기 때문에 그러한 코드를 알맞은 운영체제에 맞게 변환되도록 해주는 코드

<h5> JDK 설치 후 환경변수 설정  </h5>
- 경로지정을 따로 하지 않았을 경우 "C:\Program Files\Java" 위치에 설치되었을 것이다.
- 키보드의 윈도우키(검색) 클릭 후 "환경 변수"를 검색하여 "시스템 환경 변수 편집" 클릭 하면 시스템 속성 창이 켜지고, 고급 탭에서 환경 변수로 들어간다.
- 컴퓨터 사용자에 대한 사용자 변수와 시스템 변수가 있는데 시스템 변수에서 설정을 한다. 
- 새로 만들기를 눌러 "변수 값"에 JDK가 설치된 경로를 작성(Ex. C:\Program Files\Java\jdk-1.8 ) 하고 변수명은 JAVA_HOME으로 설정한다.
- 시스템 변수에 이미 있는 Path의 편집으로 들어가 새로만들기 하여 이전 단계에서 생성한 변수명 JAVA_HOME을 활용하여 "%JAVA_HOME%bin/" 형식으로 작성하면 완료 