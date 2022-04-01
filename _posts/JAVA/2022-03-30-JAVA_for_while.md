---
layout: post
title:  "[JAVA]반복문 while, for"
subtitle: for문과 while문에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**
- [반복문](#반복문)
    1. [for loop](#1-for문)
    2. [while loop](#2-while문)
    3. [do while loop](#3-do-while문)

<br/>
<br/>

---
# 반복문
- 조건문의 결과가 false가 될때 까지 반복한다.
- 반복할 횟수가 정해져있으면 `for loop`를 사용하고 정해져있지 않으면 `while loop`를 사용한다.
- `for loop`와 `while loop`는 상호 대체가 가능하다.
<br/>


## <span style="color:#da7c7c">1. for문</span>
- **횟수**를 기준으로 코드를 작성
- 기본 문법
    ```java
    // 초기식 ; 조건식 ; 증감식
    for (int i = 0 ; i < 10 ; i++){
        // 반복할 코드
    }
    ```
- 조건문에 사용되는 변수(`i`)를 **loop 변수**라고 부른다.
- 조건문 밖에 초기식, 조건식, 증감식을 써도 괜찮다.
    ```java
    int i = 0; // 초기식
    for (; ;){
        if ( i < 10 ) {
            // 반복할 코드
            break; // 조건식
            i++; // 증감식
        }
    }
    ```
    - 이런 형식으로 사용해도 관계는 없지만 for문의 () 안에는 `;`는 무조건 써야한다.
<br/>

## <span style="color:#da7c7c">2. while문</span>
- **상태**를 기준으로 코드를 작성
- 기본 문법
    ```java
    while (조건문) {
        // 반복할 코드
    }
    ```
<br/>

## <span style="color:#da7c7c">3. do while문</span>
- 기본 문법
    ```java
    do {
        // 반복할 코드
    } while (조건식);
    ```
- `while`과 `do while`의 차이점
    - `while` : 조건을 확인한 후 실행을 한다. 최소 0번 실행
    - `do while` : 1번 실행한 후 조건을 확인한 후 실행을 한다. 최소 1번 실행
<br/>
