---
title: Study_Spring-Web-MVC2
category: Spring Web MVC2
tag: thymleaf, message, internationlaization, validation, cookie, session, Login(filter, intercepter, error, api error)
Author: Jung
---

## **Table of Contetns**

---

</br>

- [**Table of Contetns**](#table-of-contetns)
  - [**Section1 타임 리프 기본 기능**](#section1-타임-리프-기본-기능)
    - [**Section1 프로젝트 생성**](#section1-프로젝트-생성)
    - [**기본 표현식**](#기본-표현식)
  - [**Section2 타임리프 - 스프링 통합과 폼**](#section2-타임리프---스프링-통합과-폼)
  - [**Section3 메시지 - 국제화**](#section3-메시지---국제화)
  - [**Section4 검증1 - validation**](#section4-검증1---validation)
  - [**Section5 검증2 - Bean Validation**](#section5-검증2---bean-validation)
  - [**Section6 로그인 처리1 - 쿠키 세션**](#section6-로그인-처리1---쿠키-세션)
  - [**Section7 로그인 처리2 필터, 인터셉터**](#section7-로그인-처리2-필터-인터셉터)
  - [**Section8 예외 처리와 오류 페이지**](#section8-예외-처리와-오류-페이지)
  - [**Section9 API 예외 처리**](#section9-api-예외-처리)
  - [**Section10 스프링 타입 컨버터**](#section10-스프링-타입-컨버터)
  - [**Section11 파일 업로드**](#section11-파일-업로드)
    </br>
    </br>
    </br>

### **Section1 타임 리프 기본 기능**

</br>

#### **Section1 프로젝트 생성**

</br>

|   category   |          description          |
| :----------: | :---------------------------: |
|   Project    |            Gradle             |
|   Language   |             JAVA              |
| Spring Boot  |             2.6.4             |
|    Group     |             hello             |
|   artifact   |        thymeleaf-basic        |
|     Name     |        thymeleaf-basic        |
| Package name |        hello.thymleaf         |
|  Packaging   |              Jar              |
|     JAVA     |              11               |
| Dependencies | Spring Web, Lombok, Thymeleaf |

</br>

#### **기본 표현식**

</br>

- 간단한 표현

|  표현   |       설명       |
| :-----: | :--------------: |
| ${...}  |   변수 표현식    |
| \*{...} | 선택 변수 표현식 |
| #{...}  |  메시지 표현식   |
| @{...}  | 링크 URL 표현식  |
| ~{...}  |   조각 표현식    |

</br>

- 리터럴

|          표현           |    설명     |
| :---------------------: | :---------: |
|       'one text'        |   텍스트    |
|    0, 34, 4.0, 12.3     |    숫자     |
|       true, false       |   불리언    |
|          null           |     널      |
| one, sometext, main ... | 리터럴 토큰 |

</br>

- 문자 연산

| 표현 |        설명         |
| :--: | :-----------------: | --- | ----------- |
|  +   |     문자 합치기     |
|      | the name is ${name} |     | 리터럴 대체 |

</br>

- 산술 연산

|    표현    |       설명       |
| :--------: | :--------------: |
| +,-,\*,/,% | binary operators |
| Minus sign |        -         |

</br>

- 불리언 연산

|  표현   |       설명       |
| :-----: | :--------------: |
| and, or | binary operator  |
| !, not  | boolean negation |

</br>

- 비교와 동등

|              표현              | 설명 |
| :----------------------------: | :--: |
| >,<, >=, <= , (gt, lt, ge, le) | 비교 |
|         ==, != (eq,ne)         | 동등 |

</br>

- 조건 연산

|     표현     |            설명            |
| :----------: | :------------------------: |
|   if-then    |       (if) ? (then)        |
| if-then-else |   (if) ? (then) : (else)   |
|   Default    | (value) ? : (defaultvalue) |

</br>

- 특별한 토큰
  - No-operation : \_

</br>
</br>
</br>

### **Section2 타임리프 - 스프링 통합과 폼**

</br>
</br>
</br>

### **Section3 메시지 - 국제화**

</br>
</br>
</br>

### **Section4 검증1 - validation**

</br>
</br>
</br>

### **Section5 검증2 - Bean Validation**

</br>
</br>
</br>

### **Section6 로그인 처리1 - 쿠키 세션**

</br>
</br>
</br>

### **Section7 로그인 처리2 필터, 인터셉터**

</br>
</br>
</br>

### **Section8 예외 처리와 오류 페이지**

</br>
</br>
</br>

### **Section9 API 예외 처리**

</br>
</br>
</br>

### **Section10 스프링 타입 컨버터**

</br>
</br>
</br>

### **Section11 파일 업로드**

</br>
</br>
</br>
