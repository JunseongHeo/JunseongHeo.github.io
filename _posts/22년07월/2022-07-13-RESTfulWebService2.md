---
layout: single
title: RESTful Web Services 개발_Section02
categories: RESTful
# git, study, diary, java, toDolist, cooking, plan, html, academy, html/css, JSP, RESTful
tag: [RESTful] 
---

# RESTful Web Services 개발

## Section 02 : User Servie API 추가

### User Domatin 생성 (도메인주소가 아닌 특정 정보)

User
~~~java
package com.example.restfulwebservice.user;

import lombok.AllArgsConstructor;
import lombok.Data;

import java.util.Date;

@Data
@AllArgsConstructor
public class User {
    private Integer id;
    private String name;
    private Date joinDate;

}
~~~

UserDaoService
~~~java
package com.example.restfulwebservice.user;

import java.util.ArrayList;
import java.util.Date;
import java.util.List;


public class UserDaoService {
    private static List<User> users = new ArrayList<>();

    private  static int usersCount = 3;
    static {
        users.add(new User(1, "Kenneth", new Date()));
        users.add(new User(2, "Alice", new Date()));
        users.add(new User(3, "Elena", new Date()));
    }

    public List<User> findAll() {
        return users;
    }
    public User save(User user) {
        if (user.getId() == null) {
            user.setId(++usersCount);
        }
        users.add(user);
        return user;
    }

    public User findOne(int id) {
        for (User user: users) {
            if(user.getId() == id) {
                return user;
            }
        }
        return null;
    }

}
~~~


### GET

클래스 스테레오타입 어노테이션으로 선언

생성자를 통한 의존성 주입


### POST

개발자코드 - 네트워크 - 리로드 - header : 상태코드 확인가능
URI가 같더라도 작동하는 방식(Get, POST)가 다르기때문에
서로 다른동작을 하게 할 수 있음

### Exception Handling


### DELETE
