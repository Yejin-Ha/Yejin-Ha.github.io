---
layout: post
title:  "[JAVA] try catch(예외처리)"
categories: tech
tags: java
comments: true
mathjax: true
---
**Contents**

<br/>
<br/>

---
# Exception (예외)
예외란 사용자의 잘못된 조작 또는 개발자의 잘모소딘 코딩으로 인해 발생하는 프로그램 오류이다.

예외가 발생하면 프로그램이 종료된다. 
이를 방지하기 위해 예외처리를 통해 프로그램이 종료되지 않고 정상적으로 작동되게 만들 수 있다.

Java에서는 try catch문을 통해 예외처리를 한다.

예외는 **Checked Exception, Unchecked Exception**으로 나눌 수 있다.

## Checked Exception 체크 예외
RuntimeException의 하위 클래스가 아니면서 **Exception** 클래스의 하위 클래스들이다.

체크 예외는 반드시 **에러 처리(try catch문 또는 throw)를 해야하는 특징**을 갖고 있다.

`throws`를 붙여야 사용 가능하다. throws를 사용하지 않아도 try catch문으로 예외 처리가 가능하지만 이것은 추천하지 않는다.

<br/>

## Unchecked Exception 언체크 예외
**RuntimeException**의 하위 클래스들을 의미한다. 말 그대로 실행 중에 발생할 수 있는 예외를 의미한다.

체크 예외와 달리 에러 처리(try catch)를 강제하지 않는다. 즉, try catch로 예외를 잡거나 throw로 호출한 메서드에게 예외를 던지지 않는다.

<br/>

## 여러가지 예외들

|Exception|발생 이유|
|:---:|---|
|ArithmeticException|정수를 0으로 나눌경우 발생|
|ArrayIndexOutOfBoundsExcetion|배열의 범위를 벗어난 index를 접근할 시 발생|
|ClassCastExcetion|변환할 수 없는 타입으로 객체를 반환 시 발생|
|NullPointException| 존재하지 않는 레퍼런스를 참조할때 발생|
|IllegalArgumentException|잘못된 인자를 전달 할 때 발생|
|IOException입출력 동작 실패 또는 인터럽트 시 발생|
|OutOfMemoryException|메모리가 부족한 경우 발생|
|NumberFormatException|문자열이 나타내는 숫자와 일치하지 않는 타입의 숫자로 변환시 발생|

<br/>
<br/>

# try catch문 (예외처리)
## 기본 구성
- `try {}` : 예외가 발생되는 영역
- `catch(e) {}` : 발생되는 예외를 잡아 처리하는 영역
    - 모든 예외의 부모는 Exception이기 때문에 딱히 처리할 필요는 없지만 예외를 잡아야하는 경우에 마지막 catch에 `Exception e`를 통해 모든 예외를 관리할 수 있다.
    - 자주 사용되는 메서드
        - `e.getMessage()` : 발생한 예외 클래스의 인스턴스에 저장된 메세지를 얻을 수 있음. 기본적인 내용만 알 수 있어서 상세하지 않다.
        - `e.printStackTrace()` : 발생한 예외 클래스의 가장 자세한 예외 정보를 제공한다.
- `finally {}` : 예외 발생 여부와 관계 없이 무조건 실행되는 영역
    - 선택적으로 사용한다.
    - **자원을 해제하는 용도**로 사용된다.
    - `catch` 뒤에 붙이거나 `try` 뒤에 붙일 수 있다.

```java
try {
    // 예외가 발생되는 영역
} catch (Exception e) {
    // 발생된 예외를 잡아 처리하는 영역
    System.out.println(e.getMessage()); // 발생한 예외의 기본 정보 출력
    e.printStackTrace(); // 발생한 예외의 자세한 정보 출력
} finally {
    // 예외 발생과 관계 없이 무조건 실행
}
```

<br/>
<br/>

## 다른 예외처리 방법 : throw, throws
- `throw` : 예외 객체를 고의로 발생시킬 때 사용하는 키워드
    - 억지로 에러를 발생시킬 때도 사용되지만 현재 메소드의 예외를 처리한 후에 상위 메소드에 에러 정보를 줌으로 상위 메소드에서도 에러가 발새앟ㄴ 것을 감지할 수 있다.
- `throws` : 메서드에서 발생되는 예외를 자신을 호출한 상위 메소드로 예외를 보내준다.(예외를 전가한다.)
    - 상위 메서드에서 try catch문을 통해 예외처리

```java
if (x == null) {
    throw new NullPointerException();
}
```



