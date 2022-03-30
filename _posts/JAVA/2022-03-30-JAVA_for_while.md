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
    1. [while loop](#1-while문)
    2. [for loop](#2-for문)

<br/>
<br/>

---
# 반복문
- 조건문의 결과가 false가 될때 까지 반복한다.
- 반복할 횟수가 정해져있으면 `for loop`를 사용하고 정해져있지 않으면 `while loop`를 사용한다.
<br/>

## <span style="color:#da7c7c">1. while문</span>
- 기본 문법
    ```java
    while (조건문) {
        // 반복할 코드
    }
    ```
<br/>

## <span style="color:#da7c7c">2. for문</span>
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
