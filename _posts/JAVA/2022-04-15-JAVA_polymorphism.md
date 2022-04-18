---
layout: post
title:  "[JAVA] 다형성(Polymorphism)이란?"
subtitle: 객체지향 프로그램의 다형성
categories: tech
tags: java
comments: true
---
**Contents**
- [다형성이란?](#다형성polymorphism이란)
1. [UpCasting](#1-upcasting)
2. [DownCasting](#2-downcasting)
<br/>
<br/>

---
# 다형성(Polymorphism)이란?
하나의 형태가 여러 형태로 만들어지고 사용될 수 있는 특성

<br/>

## <span style="color:#da7c7c">1. Upcasting</span>
서브 클래스의 객체가 슈퍼 클래스 타입으로 형변환 되는 것을 말한다.

즉, 부모 클래스를 상속받은 자식 클래스가 존재할 때 부모 클래스 참조 변수를 자식 클래스로 초기화하는 경우를 말한다.
```java
class 삼각형 extends 도형{}

public static void main(String[] args) {
    도형 a = new 도형();
    도형 b = new 삼각형(); // 업캐스팅
}
```
삼각형 클래스는 도형 클래스를 상속받기 때문에 삼각형 객체 안에는 도형 클래스의 멤버들이 존재하기 때문에 도형 참조 변수 b를 초기화할 수 있다.

<br/>
<br/>

## <span style="color:#da7c7c">2. Downcasting</span>
자신의 고유한 특성을 잃은 서브 클래스의 객체를 다시 복수시켜주는 것을 말하며 업캐스팅 된 것을 다시 원상태로 돌리는 것이다.
```java
class 삼각형 extends 도형{}

public static void main(String[] args) {
    도형 a = new 도형();
    도형 b = new 삼각형(); // 업캐스팅

    삼각형 da = (삼각형)a; // 다운캐스팅
    삼각형 db = (삼각형)b; // 다운캐스팅
}
```
다운캐스팅을 할 경우 모든 객체에 경고문이 나온다.

이는 JVM이 실행되기 전까지는 해당 객체가 업캐스팅 된 객체인지 아닌지 모르기 때문에 사용자에게 확인하기 위해 알려주는 것이다.
