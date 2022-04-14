---
layout: post
title:  "[JAVA] Arrays 클래스"
subtitle: java.util.Arrays 클래스에 대한 정리
categories: tech
tags: java
comments: true
mathjax: true
---
**Contents**
- [sort()](#1-arrayssort배열-구간-메소드)
- [copytOf()](#2-arrayscopyof배열-길이-메소드)
- [toString()](#3-arraystostring배열-메소드)
- [copyOfRange()](#4-arrayscopyofrange배열-시작인덱스-마지막인덱스-메소드)
<br/>
<br/>

---
# Arrays 클래스
- java.util 패키지에 존재하는 클래스이다.
- 배열을 다루기 위한 다양한 메소드가 존재한다.
- 상단에 `import java.util.Arrays;`를 통해 불러와서 사용 가능하다.
<br/>

### **<span style="color:#da7c7c">1. Arrays.sort(배열, 구간) 메소드</span>**
- 매개변수
    - 배열 - 원본 배열
    - 구간(시작 index, 마지막+1 index) - 정렬 범위를 설정할 수 있으며 입력하지 않으면 모든 원소를 정렬한다.
        - 시작 index - 정렬을 시작할 index
        - 마지막+1 index - 정렬할 원소의 마지막 index
<br/>
<br/>

전달받은 배열에서 원소들을 **오름차순**으로 정렬한다.

배열을 **내림차순**으로 정렬하려면 인자에 추가로 Collections 클래스에 `Collections.reverseOrder()`을 전달하면 된다.
<br/>

```java
import java.util.Arrays;
import java.util.Collections;
...
int[] arr1 = {4, 5, 2, 3};
String[] arr2 = {"A", "B", "Z", "T", "D"};
int[] arr3 = {9, 5, 7, 8, 9, 5, 3, 1};
int[] arr4 = {1, 2, 3, 4, 5};

Arrays.sort(arr1); // arr 배열을 오름차순으로 정렬
Arrays.sort(arr2);

Arrays.sort(arr3, 3, 7); // 3 ~ 6 index의 원소만 정렬

// error 발생!!!!
Arrays.sort(arr4, Collections.reverseOrder());

// 실행 결과 ===========
// arr1 = {2, 3, 4, 5};
// arr2 = {"A", "B", "D", "T", "Z"};
// arr3 = {9, 5, 7, 3, 5, 8, 9, 1};
```
<br/>

만약 위와 같이 실행할 경우 `Arrays.sort(arr4, Collections.reverseOrder());`에서 아래와 같은 오류가 발생할 것이다.
```
The method sort(int[]) in the type Arrays is not applicable for the arguments (int[], Collections.reverseOrder())
```

`Collections.reverseOrder()`은 <u>객체에만 사용이 가능</u>한 메소드이다.

하지만 arr4는 기본 자료형(primitive type)인 int 타입이기 때문에 적용이 불가능하다.

- 해결 방법
    - `int[]`가 아닌 `Integer[]`을 통해 객체로 선언하면 된다.

    ```java
    import java.util.Arrays;
    import java.util.Collections;
    ...
    Integer[] arr4 = {1, 2, 3, 4, 5};

    Arrays.sort(arr4, Collections.reverseOrder());
    // 실행 결과 ===========
    // arr4 = {5, 4, 3, 2, 1};
    ```
<br/>

### **<span style="color:#da7c7c">2. Arrays.copyOf(배열, 길이) 메소드</span>**
- 매개변수
    - 배열 - 원본 배열
    - 길이 - 새로 생성할 배열의 크기
<br/>
<br/>

전달받은 배열을 전달받은 길이의 새로운 배열로 생성해서 반환한다.

- 새롭게 생성된 배열의 길이가 원본 배열보다 길면, 나머지 요소는 배열의 자료형에 맞게 기본값으로 채워진다.
- 새롭게 생성된 배열의 길이가 원본 배열보다 작으면, 해당 길이까지의 요소만 반환한다.

```java
int[] arr1 = {1, 2, 3}; // 크기가 3인 int형 배열 arr1 생성

// arr1와 동일한 원소를 가지며 크기가 5인 배열 생성
int[] arr2 = Arrays.copyOf(arr1, 5);

// arr1와 동일한 원소를 가지며 크기가 2인 배열 생성
int[] arr3 = Arrays.copyOf(arr1, 2);

// 실행 결과 ===========
// arr1 = {1, 2, 3};
// arr2 = {1, 2, 3, 0, 0};
// arr3 = {1, 2};
```
<br/>

### **<span style="color:#da7c7c">3. Arrays.toString(배열) 메소드</span>**
- 매개변수
    - 배열 - 값을 출력할 배열
<br/>
<br/>

매개변수로 전달받은 배열에 정의된 값들을 문자열 형태로 만들어서 반환해준다.

```java
import java.util.Arrays;

...

int[] arr = {1, 2, 3};
System.out.println(Arrays.toString(arr));

// 실행 결과 ===========
// [1, 2, 3]
```
<br/>

### **<span style="color:#da7c7c">4. Arrays.copyOfRange(배열, 시작인덱스, 마지막인덱스) 메소드</span>**
- 매개변수
    - 배열 - 원본 배열
    - 시작 인덱스 - 배열을 자를 인덱스의 위치
    - 마지막 인덱스 - 입력된 숫자 -1 까지 배열을 분리함
<br/>
<br/>

입력받은 배열을 시작 인덱스 부터 마지막 인데스 -1 까지의 값의 배열을 반환한다.

원본 배열을 수정하는 것이 아니고 새로운 배열을 생성해서 반환한다.

```java
import java.util.Arrays;

int[] arr1 = {1, 2, 3, 4, 5, 6, 7};
int[] arr2 = Arrays.copyOfRange(arr, 3, arr.length);

System.out.println(Arrays.toString(arr1));
System.out.println(Arrays.toString(arr2));
// 실행 결과 ===========
// [ 1, 2, 3, 4, 5, 6, 7]
// [ 4, 5, 6, 7]
```
