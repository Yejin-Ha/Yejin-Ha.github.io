---
layout: post
title:  "[JAVA] 자료형, 변수, 형변환"
subtitle: 자료형, 변수, 형변환에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**
- [자료형](#자료형) 
    1. [논리형](#1-논리형)
    2. [정수형](#2-정수형)
    3. [실수형](#3-실수형)
    4. [클래스형](#4-클래스형)
- [JAVA의 변수](#java의-변수) 
    1. [변수](#1-변수)
    2. [상수](#2-상수)
- [형변환](#형변환) 
    1. [자동 타입 변환](#1-자동-타입-변환)
    2. [명시적 타입 변환](#2-명시적-타입-변환)


<br/>
<br/>

---
# 자료형
- **Primitive type** : 논리형, 정수형, 실수형 
- **class type** : 클래스형

## <span style="color:#da7c7c">1. 논리형</span>
- `boolean`
- true 또는 false 값만 들어갈 수 있음

## <span style="color:#da7c7c">2. 정수형</span>
- `byte`
    - 8 bit로 이루어져 있음(00000000 ~ 11111111)
    - unsigned에서는 범위가 0 ~ 255 이고, signed에서는 범위가 -128 ~ 127 이다.
- `short` - 사용하지 않음
- `char` - **unsigned**, 2byte
    - ASCII code(1byte)는 전세계 언어를 표현할 수 없음
    - UNICODE(2byte)를 통해서 전세계 언어를 표현한다.
    - UNICODE가 2byte라서 이를 포함하기 위해서 char는 2byte이다.
- `int` - 4byte
    - 첫 번째 bit를 **부호비트**라고 부른다.
        - **부호비트** : 맨앞의 자리를 부호로 사용하며 `0` = 양수, `1` = 음수로 인식한다.
- `long` - 8byte

> <SPAN STYLE="font-weight:bold">unsigned</span> : 부호가 없는 형식(양수만 표현 가능)  
> <SPAN STYLE="font-weight:bold">signed</span> : 부호가 있는 형식(양수, 음수 모두 표현 가능)  
> <SPAN STYLE="font-weight:bold">overflow</span> : 데이터가 범위를 초과하는 경우  
>> signed Int 변수(-128 ~ 127)에 128 값을 넣으면 값을 초과해서 -128로 인식된다.  
> <SPAN STYLE="font-weight:bold">underflow</span> : 데이터가 범위에 미치지 못하는 경우에 발생
>> signed Int 변수(-128 ~ 127)에 -130 값을 넣으면 범위에 미치지 못해서 126으로 인식된다.


## <span style="color:#da7c7c">3. 실수형</span>
- `float` - 4byte
- `long` - 8byte

## <span style="color:#da7c7c">4. 클래스형</span>
- 클래스형은 기본형과 다르게 객체를 참조하는 형태

<br/>
<br/>
<hr>

# JAVA의 변수
메모리에 공간을 할당해서 하나의 값을 할당하는 것

## <span style="color:#da7c7c">1. 변수</span>
- 값이 변경될 수 있는 경우
- 변수 생성 방법
    1. 변수를 자료형과 함께 선언한 후 값을 초기화하기
        - 초기화 : 선언된 변수에 값을 대입하는 것

        ```java
        // 변수 선언
        int age;

        // 변수 초기화
        age = 25;
        ```

    2. 선언과 초기화 한번에 하기

        ```java
        int age = 25;
        ```
- 변수가 선언되면 메모리에는 쓰레기 값이 자동으로 저장된다. JAVA에서는 쓰레기 값이 들어있는(초기화가 되지 않은) 변수를 사용할 수 없다.


## <span style="color:#da7c7c">2. 상수</span>
상수의 특징은 다음과 같다.
- 값을 변경할 수 없는 경우의 변수
- 상수명은 모두 대문자를 쓰고 Snake case를 사용한다.
- `final` 예약어를 통해 상수 선언 가능

<br/>

- 상수 생성 방법
    1. 선언과 초기화를 같이 한다.
        ```java
        class Test {
            final int TEST_N = 3;
        }
        ```
    2. 선언만 한 후 생성자를 통해 초기화한다.
        ```java
        class Test {
            final int TEST_N;

            Test() {
                TEST_N = 3;
            }
        }
        ```

<br/>
<br/>


`public static final`와 `public final`는 차이가 존재한다.

`static`을 사용하면 클래스가 메모리에서 실행되면서 초기화 과정이 필요 없이 static이 선언된 변수와 메서드에 바로 접근이 가능하다.

만약 `static`을 사용하지 않고 상수를 선언한다면 해당 클래스로 객체를 생성할 때 마다 상수를 새로 만든다.

그렇기 때문에 `public static final`을 통해 메모리에 한 번만 값을 올려놓는 것을 선호한다.

> <span style="background-color:#fffdd6">💡 static에 관한 설명은 <A href="https://yejin-ha.github.io/tech/2022/04/13/JAVA_static_final/#static">여기</A>를 참고하면 된다.</span>

<br/>
<br/>
<hr>

# 타입변환 형변환
변수의 타입이 다른 타이브올 변경되는 것

## <span style="color:#da7c7c">1. 자동 타입 변환</span>
- 연산시 컴파일러가 자동으로 수행하는 타입 변환
- 사용자가 강제로 타입 변환을 하지 않는 경우
    ```java
    int a = 1;
    double b = 3.0;

    a + b => double 형이 된다.
    ```
    - 4byte인 int와 8byte인 double이 연산되면 자동으로 큰 byte의 자료형으로 변환된다.

## <span style="color:#da7c7c">2. 명시적 타입 변환</span>
- **강제 타입 변환**이라고도 한다.
- 변환시키고자 하는 데이터 앞에 `(타입)`을 붙인다.
    - **cast 연산자**
    ```java
    short a = 10; // 00000001 00000001
    byte a1 = a; // error 발생. 16bit를 8bit에 담을 수 없음

    byte a1 = (byte)a; // error 발생 X
    // a1 => 00000001이 될 것이다. 
    // 앞에 byte가 버려지고 뒷 byte만 들어간다.
    ```

