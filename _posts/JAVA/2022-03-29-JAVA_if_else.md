---
layout: post
title:  "[JAVA]조건문(if, else if, else)"
subtitle: if, else if, else 문에 대해 정리
categories: tech
tags: java
comments: true
---
**Contents**
- [자료형](#자료형)
- [JAVA의 변수](#java의-변수)
- [형변환](#형변환)


<br/>
<br/>

---
# 조건문
조건에 따라 코드의 실행 흐름을 다르게 동작하도록 제어하는 것

## if문
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
