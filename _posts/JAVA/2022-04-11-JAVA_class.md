---
layout: post
title:  "[JAVA] class란?"
subtitle: 클래스에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**
- [Class란?](#class)
- [Class 명명 규칙](#1-클래스-명명-규칙)
- [Class의 멤버 구성](#2-클래스-멤버-구성) - field, constructor, method
- [예시](#3-예시)

<br/>
<br/>

---
# Class
자료형 중 하나로 객체를 정의해 놓은 것이다.

**관련 있는 속성과 행위(기능)**를 묶음(멤버)으로 관리한다.

하나의 클래스 파일(.class)에는 반드시 하나의 자바 클래스만 포함되어야 한다.
<br/>
<br/>

## <span style="color:#da7c7c">1. 클래스 명명 규칙</span>
1. 하나 이상의 문자로 이루어져야 한다.
2. 첫 번째 글자에는 숫자가 올 수 없다.
3. 첫 번째 글자는 대문자로 작성한다.
4. 자바 명령어, 키워드는 사용할 수 없다.(while, for, int 등)
5. $, _ 외에는 특수문자 사용 불가능

<br/>
<br/>

## <span style="color:#da7c7c">2. 클래스 멤버 구성</span>
**필드(field), 생성자(constructor), 메서드(method)**로 이루어져 있다.
이 구성 멤버들은 생략되거나 여러 개 작성될 수 있다.

- **필드** : 객체의 데이터가 저장되는 곳
    - 변수의 선언과 비슷하지만 변수는 생성자와 메소드 내에서만 사용되고 생성자와 메소드가 종료되면 자동으로 소멸된다.
    - 클래스 선언 바로 아래에 선언되며, 생성자와 메소드보다 위에 선언된다.
    ```java
    class TV{
        // field 자리
        boolean power;
        int channel;
    }
    ```
<br/>

- **생성자**
    - **객체를 초기화 하기 위해 사용**한다.
    - 클래스명과 동일한 이름의 멤버 메소드
    - **객체 생성 시 반드시 호출된다**(ex. `new Info()`)
    - 인자가 없는 생성자를 **default constructor**라고 부른다.
        - 디폴트 생성자는 따로 정의하지 않아도 JVM이 알아서 호출 해준다.
    - 오버로딩이 가능하다. => 객체 생성하는 방법을 다양하게 제공할 수 있다.
        - 오버로딩할 경우 default 생성자를 명시하지 않으면 default 생성자는 사용할 수 없다.
        - `Info(String s){...}`만 오버로딩할 경우 -> `new Info()`는 에러 발생
    ```java
    // Info class
    public class Info() {
            // field
            private String name;
            private int age;

            // Default Constructor
            Info() {
                System.out.println("hi");
            }
            // constructor overloading
            Info(String n, int a) {
                this.name = n;
                this.age = a;
            }
            ...
    }
    ```
<br/>

- 메소드
    - 객체의 행위를 설정하는 곳
    ```java
    class TV {
        ...
        // 메소드 영역
        void view(){
            System.out.println("TV의 화면입니다.");
        }
    }
    ```
<br/>
<br/>

## <span style="color:#da7c7c">3. 예시</span>
- Info class
    ```java
    class Info {
        String name;
        int age;

        String infoToString() {
            return "Info[name = " + name + ", age = " + age + "]";
        }
    }
    ```
<br/>

- main class
    ```java
    public static void main(String[] args){
        // Info는 클래스 자료형이라서 배열의 자료형이 될 수 있다.
        Info[] infos = new Info[2];

        // Info 객체 생성
        infos[0] = new Info();
        infos[0].name = "홍길동";
        infos[0].age = 20;

        infos[1] = new Info();
        infos[1].name = "이순신";
        infos[1].age = 30;

        System.out.println(infos[0].infoToString());
        System.out.println(infos[1].infoToString());
    }
    ```
