---
layout: post
title:  "[JAVA]조건문 if, switch"
subtitle: if문과 swirch문에 대해 정리
categories: tech
tags: java
comments: true
---
**Contents**
- [조건문](#조건문)
    1. [if 문](#1-if문)
    1. [switch 문](#2-switch문)

<br/>
<br/>

---
# <span style="color:#da7c7c">조건문</span>
조건에 따라 코드의 실행 흐름을 다르게 동작하도록 제어하는 것

## <span style="color:#da7c7c">1. if문</span>
- 기본 문법
    - `else if`와 `else`는 선택적으로 사용 가능하다.
    ```java
    if (조건1) {
        pass
        // 조건1이 true일 경우 실행할 code
    } else if (조건2) {
        pass
        // 조건2가 true일 경우 실행할 code
    } else {
        pass
        // 모든 조건에 해당하지 않을 경우 실행할 code
        // 꼭 써야되는 코드는 아님
    }
    ```

- **삼항 연산자**를 통해 더욱 간결하게 사용이 가능하다.
    ```java
    if (a > 5) {
        b = 10;
    } else {
        b = 0;
    }

    // 삼항 연산자 사용하기
    b = (a > 5)? 10 : 0;
    ```
<br/>
<br/>

## <span style="color:#da7c7c">2. switch문</span>
- 기본 문법
    ```java
    switch (정수형 결과식) {
        case 상수: 
            // 실행할 코드
        case 상수:
            // 실행할 코드
        ...
        default :
            // 실행할 코드
    }
    ```
    - `default` : 매칭되는 case가 없는 경우에 실행되는 구문이다.
        - `if else`에서 `else`와 같은 역할을 한다.
        - 필요에 따라 선택적으로 사용하면 된다.
        

- `switch`와 `if else`의 차이점
    - `switch`는 시작 case가 정해지면 그 아래에 있는 모든 case를 실행하고 `if else`는 조건에 해당하는 경우만 실행한다.
        ```java
        int n = 1;

        switch (n) {
            case 1: System.out.print("1 ");
            case 2: System.out.print("2 ");
        }

        // 실행 결과
        1 2
        ```
    - 이를 방지하기 위해 `break`를 사용한다.
        ```java
        int n = 1;

        switch (n) {
            case 1: 
                System.out.println("1 "); 
                break; // switch, for, while 파괴
            case 2: System.out.println("2");
        }

        // 실행 결과
        1
        ```