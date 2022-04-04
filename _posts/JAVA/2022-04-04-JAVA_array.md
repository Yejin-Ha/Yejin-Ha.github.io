---
layout: post
title:  "[JAVA]배열 Array"
subtitle: 배열에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**
1. [배열](#array-배열)
    - [배열 생성 방법](#배열-생성-방법)
2. [동적, 정적바인딩](#동적-정적-바인딩)

<br/>
<br/>

---
# Array 배열
**동일한 자료형**으로 메모리에 연속으로 할당된 변수 집합

## <span style="color:#da7c7c">배열 생성 방법</span>
```java
// int 자료형의 배열 참조 변수 선언
int[] arr; 
arr = new int[5]; // int형의 5개의 값으로 이루어진 배열 r객체 arr을 선언
```
- 배열을 생성할 때는 `new` 키워드를 통해 새로 생성한다.
- 배열을 생성할 때 값을 지정하지 않으면 0에 해당하는 값(0, false, null)을 자동으로 할당한다.

<br/>

```java
// 초기화와 선언을 한번에
int[] arr1 = new int[3];
// 값을 직접 설정해서 초기화
int[] arr2 = {1, 2, 3};
// 값을 직접 설정할 경우엔 길이를 지정하지 않아도 된다.
int[] arr3 = new int[] {4, 5, 6};
```
- 만약 값을 직접 설정하는 경우에 길이도 같이 지정하면 에러가 발생한다.
    ```java
    int[] arr = new int [3] {1, 2, 3}; // error 발생
    ```
    - 값의 길이에 맞춰서 자동으로 배열의 길이가 설정된다.
        
- 이미 초기화 된 배열의 값을 변경할 수 없다.
    ```java
    int[] arr = {1, 2, 3};
    arr = {3, 2, 1}; // compile error 발생
    ```
- 이미 초기화 된 배열에 새로운 객체를 생성할 수 있다.
    ```java
    int[] arr = new int[] {4, 5, 6};
    arr = new int[] {6, 5, 4};
    ```
<br/>

`arr.length` - arr 배열의 길이를 반환

<br/>
<br/>
<hr/>

# 동적, 정적 바인딩
- **바인딩** : 프로그램에 사용된 구성 요소의 실제 값 또는 프로퍼티를 결정짓는 행위를 의미한다.

1. 정적 바인딩
    - **컴파일 타임**에 필요한 공간이 결정된다.
    ```java
    int a = 10;
    char b = 'B';
    ```

2. 동적 바인딩
    - **런타임**에 필요한 공간이 결정된다.  
        ```java
        Scanner sc = new Scanner(System.in);
        int[] arr;

        System.out.print("배열의 길이를 입력하시오.");
        int size = sc.nextInt();

        arr = new int[size];
        ```