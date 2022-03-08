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
    - [**check box**](#check-box)
    - [**radio**](#radio)
    - [**select**](#select)
    - [**ModleAttribute의 또다른 기능**](#modleattribute의-또다른-기능)
  - [**Section3 메시지 - 국제화**](#section3-메시지---국제화)
    - [**스프링 부트 메시지 소스 설정**](#스프링-부트-메시지-소스-설정)
    - [**MessageSource Interface**](#messagesource-interface)
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

```html
<!-- 자바스크립트 인라인 사용 전 -->
<script>
  var username = [[${user.username}]];
  var age = [[${user.age}]];
  //자바스크립트 내추럴 템플릿
  var username2 = /*[[${user.username}]]*/ "test username";
  //객체
  var user = [[${user}]];
</script>

<!-- 자바스크립트 인라인 사용 후 -->
<script th:inline="javascript">
  var username = [[${user.username}]];
  var age = [[${user.age}]];
  //자바스크립트 내추럴 템플릿
  var username2 = /*[[${user.username}]]*/ "test username";
  //객체
  var user = [[${user}]];
</script>

<!-- 자바스크립트 인라인 each -->
<script th:inline="javascript">
  [# th:each="user, stat : ${users}"]
  var user[[${stat.count}]] = [[${user}]];
  [/]
</script>
```

> 인라인을 사용하면 프로퍼티에 순수 해석이 아닌 타입으로 자동 변환 해줌  
> 객체도 json으로 파싱해줌

</br>
</br>
</br>

### **Section2 타임리프 - 스프링 통합과 폼**

</br>

#### **check box**

</br>

- 단일 체크 박스

</br>

```html
<!-- single checkbox -->
<div>판매 여부</div>
<div>
  <div class="form-check">
    <input
      type="checkbox"
      id="open"
      th:field="*{open}"
      class="form-check-input"
    />
    <label for="open" class="form-check-label">판매 오픈</label>
  </div>
</div>
```

</br>

> - html에서 checkbox 미 체크시 값이 넘어가지 않는 문제 -> hidden 타입 만들어야함.
> - but 타임리프에서는 th 설정자로 선택 변수로 지정하면 hidden 박스 만들어서 false로 데이터를 넘겨줌

</br>

- 다중 체크 박스

</br>

```html
<!-- multi checkbox -->
<div>
  <div>등록 지역</div>
  <div th:each="region : ${regions}" class="form-check form-check-inline">
    <input
      type="checkbox"
      th:field="*{regions}"
      th:value="${region.key}"
      class="form-check-input"
    />
    <label
      th:for="${#ids.prev('regions')}"
      th:text="${region.value}"
      class="form-check-label"
      >서울</label
    >
  </div>
</div>
```

</br>

> - item 객체가 가리키는 regions에 다중 체크박스의 value를 배열로 반환
> - each 루프에서 반복적으로 만들경우 spring에서 임의로 rigions1,2,3, id를 붙여줌
> - label은 그렇게 생성한 checkbox의 id를 이용하여 체크 가능

</br>

#### **radio**

</br>

```html
<!-- radio button -->
<div>
  <div>상품 종류</div>
  <div th:each="type : ${itemTypes}" class="form-check form-check-inline">
    <input
      type="radio"
      th:field="*{itemType}"
      th:value="${type.name()}"
      class="form-check-input"
    />
    <label
      th:for="${#ids.prev('itemType')}"
      th:text="${type.description}"
      class="form-check-label"
    >
      BOOK
    </label>
  </div>
</div>
```

</br>

- 타임리프에서 ENUM 직접 접근하기

</br>

```html
<!-- but ENUM의 패키지 위치 변경되는 경우 자바 컴파일러가 타임리프까지 컴파일 오류를 잡을 수 없음으로 추천 X -->

<div
  th:each="type : ${T(hello.itemservice.domain.item.ItemType).values()}"
></div>
```

</br>

#### **select**

</br>

```html
<!-- SELECT -->
<div>
  <div>배송 방식</div>
  <select th:field="*{deliveryCode}" class="form-select">
    <option value="">==배송 방식 선택==</option>
    <option
      th:each="deliveryCode : ${deliveryCodes}"
      th:value="${deliveryCode.code}"
      th:text="${deliveryCode.displayName}"
    >
      FAST
    </option>
  </select>
</div>
```

</br>

#### **ModleAttribute의 또다른 기능**

</br>

```java

@ModelAttribute("regions")
    public Map<String,String> regions(){
        Map<String,String> regions = new LinkedHashMap<>();
        regions.put("SEOUL","서울");
        regions.put("BUSAN","부산");
        regions.put("JEJU","제주");

        return regions;
    }

```

</br>

> 위의 코드 방식으로 ModelAttribute를 지정하면  
> controller에서 호출 될 때 객체를 자동으로 넣어서 사용할 수 있다.

</br>
</br>
</br>

### **Section3 메시지 - 국제화**

</br>

> 메시지는 여러화면에 있는 단어를 유지 보수하기 용이하도록 하기 위해  
> 다양한 메시지를 한 곳에서 관리하도록 해주는 기능
>
> 국제화는 HTTP header 중 Accept-Language 요청에 따라  
> 각 locale별로 서비스를 관리하는 것

</br>

#### **스프링 부트 메시지 소스 설정**

</br>

- application.properites

```java
spring.messages.basename=messages // default
```

</br>

> MessageSource를 스프링 빈으로 등록할 필요 X  
> 설정만 한다면 스프링부트가 MessageSource를 자동으로 스프링 빈으로 등록

</br>

- messages.properties - locale default

```java

hello=안녕
hello.name=안녕 {0}

label.item=상품
label.item.id=상품 ID
label.item.itemName=상품명
label.item.price=가격
label.item.quantity=수량

page.items=상품 목록
page.item=상품 상세
page.addItem=상품 등록
page.updateItem=상품 수정

button.save=저장
button.cancel=취소

```

- messages_en.properties

```java

hello=hello
hello.name=hello {0}

label.item=Item
label.item.id=Item ID
label.item.itemName=Item Name
label.item.price=price
label.item.quantity=quantity
page.items=Item List
page.item=Item Detail

page.addItem=Item Add
page.updateItem=Item Update
button.save=Save
button.cancel=Cancel

```

</br>

#### **MessageSource Interface**

</br>

> getMessage(String code, @Nullable Object[] args, @Nullable String defaultMessage, Locale locale)

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
