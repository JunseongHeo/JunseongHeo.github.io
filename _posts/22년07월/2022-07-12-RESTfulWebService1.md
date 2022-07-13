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

두번째 API 작성(단순히 문자열반환이 아닌 자바bean형식으로 반환)
자바bean을 반환하면 JSON 형태로 데이터 반환.
xml형태로 데이터반환하고자 하면 별도의 라이브러리 사용

// 자바빈이 뭐지?

// lombock 으로 getter setter, 생성자 편하게 포함. 코드깔끔.
롬복은 뭐하는 애인가?

포스트맨으로 테스트까지 완료

~~~
{"message":"Hello World"}
~~~


### DispatcherServlet, 프로젝트 동작 이해하기 

SpringBoot의 동작원리

application.yml  설정이름:값 // 가독성좋은 쉬운 디자인
application.properties 설정이름=값

로그출력 속성 추가


// Dispatcher 보대다. 파견하다. 발송하다.
- DispatcherServlet
사용자의 요청을 처리하는 일종의 게이트웨이

클라이언트의 모든 요청을 한곳으로 받아서 처리
요청에 맞는 Handler로 요청을 전달
Handler의 실행 결과를 Http Response 형태로 만들어서 전달.


- @RestController(@Controller + @ResponseBody)
Spring4부터는 xml파일에 설정정보를 등록하지 않고 
@으로 각종 컴포넌트 등록
View를 갖지 않는 Rest Data(JSON/XML)를 반환


### Path Variable

URI에 가변적인 변수를 지정해서 사용 가능

~~~java
@GetMapping(path = "/hello-world-bean/path-variable/{name}")
public HelloWorldBean helloWorldBean(@PathVariable String name) {
    return new HelloWorldBean(String.format("Hello World, %s", name));
}
~~~