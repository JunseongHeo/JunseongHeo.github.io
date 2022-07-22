---
layout: single
title: RESTful Web Services 개발_Section05
categories: RESTful
# git, study, diary, java, toDolist, cooking, plan, html, academy, html/css, JSP, RESTful
tag: [RESTful] 
---

# RESTful Web Services 개발

## Section 05 : JPA(Java Persistence API) 사용

### JPA의 개요

JPA(Java Persistence API)는 
자바 ORM(Object Relational Mapping 객체-관계 매핑) 기술에 대한 API 표준 명세
자바 어플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스
EntityManager를 통해 CRUD 처리

- Hibernate
JPA의 구현체. 인터페이스를 직접 구현한 라이브러리
생산성, 유지보수, 비종속성

- Spring Data JPA
스프링 모듈. JPA를 추상화한 Repository 인터페이스 제공
JPA를 보다 쉽게 사용할수 있도록 제공

### JPA 사용을 위한 의존성 추가와 설정

메이븐 의존성
~~~
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
		<dependency>
			<groupId>com.h2database</groupId>
			<artifactId>h2</artifactId>
			<scope>runtime</scope>
		</dependency>
~~~

yml 설정
~~~
jpa:
  show-sql: true
  hibernate:
    ddl-auto: create
h2:
  console:
    enabled: true

spring:
  datasource:
    url: jdbc:h2:mem:testdb
~~~

- h2 console 주소 접속
http://localhost:8088/h2-console



### Spring Data JPA를 이용한 Entitiy 설정과 초기데이터 생성

~~~java
@Entity
@Table(name="user는 예약어가 됬으니 다른 테이블명으로")
public class User {
    @Id
    @GeneratedValue
    private Integer id;
    ...
}
~~~

resources 폴더 아래 sql폴더는 데이터베이스 실행시 실행.
초기데이터 생성

### JPA Service 구현을 위한 Controller, Repository 생성




### JPA를 이용한 사용자 목록 조회 - GET HTTP Method

### JPA를 이용한 사용자 추가와 삭제

### 게시물 조회를 위한 POST Entity와 User Entitiy와의 관계 설정

### JPA를 이용한 새 게시물 추가 - POST HTTP Method