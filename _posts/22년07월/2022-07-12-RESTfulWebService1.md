---
layout: single
title: RESTful Web Services 개발_Section00~06
categories: RESTful
# git, study, diary, java, toDolist, cooking, plan, html, academy, html/css, JSP, RESTful
tag: [RESTful] 
---

# RESTful Web Services 개발

## Section 00 : 개념이해

### Web Service와 Web Application의 이해

웹 서비스 : 네트워크 상에서 서로 다른 종류의 컴퓨터들 간에 상호작용하기 위한 소프트웨어 시스템

웹 어플리케이션 : 서버에 저장되어있고, 웹브라우저를 통해 실행할 수 있는 프로그램. 클라이언트의 요청(input)을 처리하기 위한 프로그램. 요청을 받아 처리하고 응답(output)해주는 동적인 페이지 구현.

웹 서비스 정의 
- Request/Response Format
- Request Structure
- Response Structure
- Endpoint(URL..)

데이터 교환 포멧 
- XML : </>
- JSON : {...}

### SOAP와 REST 이해

웹서비스 개발 방법 2가지
- SOAP (Simple Object Access Protocol) : XML로 주고받음
복잡한구조. 무겁고 느리다. 

- RESTful (REpresentational State Transfer) : resource의 representation에 의한 상태전달. HTTP 메서드를 통해 resource를 처리하기 위한 아키텍처.

resource  
- URI, 인터넷 자원을 나타내는 유일한 주소. 
- XML, HTML, JSON


## Section 01 : Spring Boot로 개발하는 RESTful Service

### Spring Boot 개요

단독실행 가능하고 상용화 수준의 스프링 기반 어플리케이션을 쉽게 만들 수 있다. 실행을 위한 별도의 서버 설치 불필요(내장 서버로 구동)
스프링만 사용했을 때 필요한 많은 설정작업을 단축시켜줌.


### REST API 설계

RESTful Web Services

| 설명 | REST API | HTTP 메서드 |
|:--:|:--:|:--:|
| 모든 유저 조회 | /users | GET |
| 유저 생성 | /users | POST |
| 한 유저 조회 | /users/{id} | GET |
| 한 유저 삭제 | /users/{id} | DELETE |


### Spring Boot Project 생성, 실행

postman : API 테스트 플랫폼

SpringBoot initializer로 Maven프로젝트 생성
(의존성 : SpringBootDevTools, Lombok, SpringWeb, SpringDataJPA, H2)

IntelliJ에 프로젝트 생성

클래스 실행

prosperties -> yml 파일로 변경
server:
    port: 8088로 변경


### HelloWorld Controller 추가

Get메서드 방식으로 Controller에 메핑
페이지 서버에 전송

브라우저로 페이지 확인.
포스트맨으로 테스트

### HelloWorld Bean 추가


### DispatcherServlet, 프로젝트 동작 이해하기 


### Path Variable