---
layout: post
title:  "변수명 규칙"
date:   2023-05-15 12:00
categories: Java
thumbnail: /assets/img/posts/java.png
Authors : Hwet
tags: Static Instace
comments: 1
---
## 변수명을 설정하는 방법
1. 스네이크(snake) 케이스 : 모든 문자는 소문자로 표기하고 언더바(_)가 들어 있는 표현방식이 뱀처럼 생겼다고 하여 스네이크 케이스라고 한다.
    - > String variable_name;
2. 카멜(camel) 케이스 : 중간 글자들은 대문자로 시작하고 첫 글자는 소문자로 표기한 표현 방식이 낙타와 모양이 비슷하다고 하여 카멜 케이스라고 한다.
    - > String variableName;
3. 파스칼(Pascal) 케이스 : 첫 글자와 중간 글자들이 대문자인 표기법으로 파스칼 언어의 표기법과 비슷하다고 하여 파스칼 케이스라고 한다.
    - > String VariableName;
4. 케밥(kebab) 케이스 :  모든 문자를 소문자로 표기하고 하이픈(-)으로 연결하여 표기한 방법이 케밥이 꼬챙에에 꽃힌 모습과 비슷하다고 하여 케밥 케이스라고 한다.
   - > String variable-name;

## 변수명 표기법을 따라야하는 이유(팀에 속해있으면 팀의 규칙을 따랴야함)
1. 일정한 규칙없이 변수명을 만들다보면 혼란을 야기할 수 있다. 
2. 협업시에 규칙없이 명명하게 되면 다양한 변수가 나올 수 있기 때문 