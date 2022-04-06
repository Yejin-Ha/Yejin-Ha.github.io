---
layout: post
title:  "[JAVA] String class"
subtitle: String class에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**<br/>
String 변수를 비교할 경우 `==` 연산자가 아닌 `.equals()` 메소드를 사용한다.
<br/>
<br/>

---
# String
class 형 자료형이다.

int, float, char type의 기본 자료형(primitive)은 변수를 비교할 때 `==` 연산자를 통해 비교를 하지만 String type의 변수를 `.equals()`를 사용해야 한다.
<br/>
<br/>

## <span style="color:#da7c7c">1. == 연산자 비교</span>
```java
String n1 = "hello";
String n2 = "welcome";
String n3 = "hello";
```
이 경우 "hello"가 들어있는 메모리를 참조하는 n1이 선언된다.

n3를 초기화하면서 이미 "hello"가 들어있는 메모리가 존재하므로 새로운 메모리를 생성하지 않고 n1이 참조한 동일한 메모리를 n3도 참조한다.

```java
System.out.println(n1 == n2); // false
System.out.println(n1 == n3); // true
```
<br/>
<br/>

## <span style="color:#da7c7c">2. .equals() 메소드 비교</span>
위와 다르게 사용자가 문자열을 입력할 경우엔 문자열이 객체로 생성된다.

```java
String n1 = "hello";
String n2 = new String("hello");
```
n2라는 새로운 String 객체를 생성하면 "hello"로 값이 같더라도 다른 메모리를 참조한다.

```java
System.out.println(n1 == n2); // false
```

이 경우에는 `str1.equals(str2)` 메소드를 통해 비교할 수 있다.
- `문자열1.equals(문자열2)` 
    - 두 문자열의 값만을 비교하는 메소드
    - 문자열1 : 위의 코드에서 n1 역할
    - 문자열2 : 위의 코드에서 n2 역할

```java
System.out.println(n1.equals(n2)); // true
System.out.println(n2.equals(n1)); // true
```

- `문자열1.equalsIgnoreCase(문자열2)`
    - `equals` 메소드와 같이 두 문자열을 비교하지만 대소문자를 구분하지 않고 비교한다.
    
    ```java
    String n1 = "HELLO";
    String n2 = new String("hello");

    System.out.println(n1.equals(n2)); // false
    System.out.println(n1.equalsIgnoreCase(n2)); // true
    ```
