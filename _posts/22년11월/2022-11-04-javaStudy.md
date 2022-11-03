---
layout: single
title: 스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술(김영한)[1.프로젝트 환경설정]
categories: JSP
# git, study, diary, java, toDolist, cooking, plan, html, academy, html/css, JSP
tag: [java] 
---

# 프로젝트 생성

gradle, 
springBoot 2.7.x,
Java 17
War

Dependencies : Spring web, Thymeleaf


# View환경설정

thymeleaf를 활용하여 templates폴더의 hello.html을 화면에 띄우려 했는데
controller에서 viewResolver로 hello.html의 경로를 못잡아주고 white페이지가 계속 뜸.

알고보니 의존성 추가할 때 엉뚱한 thymeleaf 라이브러리를 받아서
templates폴더 경로를 자동으로 못잡고 있었던거 같음

build.gradle에서 implemetation 주소를 입력해 의존성 추가를 정확하게해서 해결완료.

# 서버 배포

윈도우의 경우 해당 프로젝트로 이동
D: : D드라이브로 변경
dir : 해당 폴더 파일목록 조회
파일이름 : 해당 파일 실행

~~~
cd 해당프로젝트
cd dir          
gradlew  // 해당 프로젝트 빌드
cd build
cd libs
cd dir  // 빌드한 배포파일 조회
java -jar 빌드파일.jar // 배포파일 실행
// 종료하려면 왼쪽 하단 커서놓고 ctrl+C
~~~

참고 : foreground 배포 java -jar / background 배포 javaw -jar
http://www.praconfi.com/2021-12-10/Window-server%EC%97%90-jar-%EB%B0%B0%ED%8F%AC%ED%95%98%EA%B8%B0

참고 : background 배포 프로세스 종료방법. 포트강제종료 taskkill /pid 피드번호 /f
https://shoney.tistory.com/entry/Spring-Boot-%EC%9C%88%EB%8F%84%EC%9A%B0%EC%97%90%EC%84%9C-%EC%8B%A4%ED%96%89%EC%A4%91%EC%9D%B8-jar-%EC%A2%85%EB%A3%8C