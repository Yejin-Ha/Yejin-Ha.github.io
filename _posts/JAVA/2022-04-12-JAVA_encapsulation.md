---
layout: post
title:  "[JAVA] 캡슐화(Encapsulation)란?"
subtitle: java의 캡슐화(은닉화)에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**
- [캡슐화란?](#캡슐화란)
- [캡슐화 방법](#캡슐화-방법)

<br/>
<br/>

---
# 캡슐화란?
일반적으로 변수와 클래스를 하나로 묶는 작업을 의미한다.

캡슐화는 **중요한 데이터를 보존, 보호**하기 위해 사용된다.

즉, 클래스에 담는 내용 중 중요한 데이터나 기능을 외부에서 직접 접근하지 못하도록 사용하는 것이다.
- `private`멤버는 외부에서 값을 직접적으로 대입시킬 수 없고 객체가 제공하는 필드와 메소드를 통해서만 접근이 가능하다.
- `private` 변수에 값을 대입하기 위해서는 `public`으로 제공되는 set, get 함수를 사용해야 한다.
- set 함수에서는 `private` 멤버에 제약조건을 걸어서 예기치 않은 값에 대해 문제를 방지할 수 있다.
<br/>
<br/>

캡슐화는 **접근제어자**를 통해 이루어진다.

객체가 갖고 있는 **내부 데이터는 숨기는 것이 규칙**이다. 하지만 이 규칙을 어겨도 에러가 발생하지 않는다.

```java
// Info class
Class Info() {
    String name;
}

...

// main method
public static void main(String[] args) {
    Info i = new Info();

    // 내부 데이터를 외부에서 수정, but 오류가 발생하지 않음
    i.name = "홍길동";
}
```
<br/>
<br/>

## <span style="color:#da7c7c">캡슐화 방법</span>
1. 멤버 변수 앞에 접근제한자 `private`를 붙인다.
    ```java
    public class Test {
        private int score;
    }
    ```
2. 해당 멤버 변수에 값을 설정하고 꺼내올 수 있는 메소드를 만든다.(`setter` / `getter`)
    - `getter` : 멤버 필드의 값을 반환하는 멤버 메소드
    - `setter` : 멤버 필드의 값을 설정하는 멤버 메소드

    ```java
    public class Test {
        private int score;

        void setScore(int n) {
            score = n;
        }

        int getScore() { 
            return score;
        }
    }
    ```

- 실행

```java
public static void main(String[] args) {
    // private 멤버가 존재하는 Test 객체 생성 & 초기화
    Test t = new Test();

    // Test의 score은 직접 접근이 불가능함으로 에러 발생
    t.score = 100;

    // setter 메소드를 통해 값을 설정한다.
    t.setScore(100);

    System.out.println(t.getScore);
}

// 실행 결과 =========
// 100
```
