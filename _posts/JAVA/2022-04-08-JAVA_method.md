---
layout: post
title:  "[JAVA] Method 메서드"
subtitle: 메서드에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**

<br/>
<br/>

---
# <span style="color:#da7c7c">Method 메서드</span>
java에서는 함수를 메서드라고 부른다.

자주 사용하는 코드를 정의해두고 필요할 때마다 호출(call)해서 사용한다.

## **Method 구조**
```java
[접근제한자] [예약어] 반환자료형 메서드명(매개변수들...) throws 예외클래스명 {
    문장;
    [return; or return 반환값;]   
}
```
- 반환자료형 : 반환할 값의 자료형을 작성한다.
    - primitive type, class type 모두 작성 가능
    - `void` : 반환할 값이 없을 경우에 작성
- 메서드명 : 명명법을 고려하고 기능을 명시해서 작성한다.
    - camel-case를 사용한다.(ex. helloWorld)
- 매개변수 : 메서드가 동작하기 위해 필요한 값을 받는 변수
    - 매개변수에 따라 **오버로딩**이 가능하다.
- `return` : 메서드의 **종료를 의미한다.**(`break`와 같은 역할)
    - 반환 자료형이 `void`일 경우엔 생략해도 된다.
    ```java
    public static void test() {
            System.out.println("출력");
            return;
            System.out.println("출력 안됨");
    }
    // ====== 실행 결과 =======
    // 출력
    ```
- 예외클래스 `throws 예외클래스명` : 예외 처리가 필요한 경우 예외를 처리하는 클래스 명명

<br/>
<br/>
<hr>

# <span style="color:#da7c7c">Method 오버로딩 Overloading</span>
한 클래스 내에 이미 사용하려는 이름과 같은 이름을 가진 메소드가 있더라도 매개변수의 개수 또는 타입이 다르면, 같은 이름을 사용해서 메소드를 정의할 수 있다.

- **조건**
    1. 메서드의 이름이 같아야 한다.
    2. 매개변수의 개수나 타입이 달라야 한다.

```java
// method 메서드 오버로딩
public static void method() {
    System.out.println("값 없음");
}

public static int method(int n) {
    System.out.println(n);
    return 10;
}
```