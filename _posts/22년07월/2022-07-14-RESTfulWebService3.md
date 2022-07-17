---
layout: single
title: RESTful Web Services 개발_Section03
categories: RESTful
# git, study, diary, java, toDolist, cooking, plan, html, academy, html/css, JSP, RESTful
tag: [RESTful] 
---

# RESTful Web Services 개발

## Section 03 : RESTful Service 기능 확장

### Validation 유효성

### internationalization 국제화/다국어처리

### XML format으로 반환하기
헤더에서 Accept - application/xml
프로그램에서 xml포멧으로 응답 못하므로 오류뜸(spirng은 기본 json포멧)

라이브러리 의존성 주입
~~~
<dependency>
    <groupId>com.fasterxml.jackson.dataformat</groupId>
    <artifactId>jackson-dataformat-xml</artifactId>
    <version>2.10.2</version>
</dependency>
~~~


### Filtering

특정 필드 단위 제어
@JsonIgnore

클래스 단위 특정 value 단위 제어
@JsonIgnoreProperties(value={"password","name"})

유저 도메인클래스에서 필터를 적용하고
@JsonFilter("UserInfo")
컨트롤러에서 필터객체 생성.
맵핑객체를 생성하여 필터객체를 받음
~~~java
FilterProvider filters = new SimpleFilterProvider().addFilter("UserInfo", filter);
MappingJacksonValue mappping = new MappingJacksonValue(user);
mappping.setFilters(filters);
~~~

### Version 관리

