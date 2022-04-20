---
layout: post
title:  "[JAVA] Object 클래스"
subtitle: java의 Object 클래스에 대한 정리
categories: tech
tags: java
comments: true
mathjax: true
---
**Contents**
- [Object 클래스란?](#object-클래스)
- [Object 클래스의 메서드](#object-class의-매서드)
- [hashCode()와 equals()](#hashcode와-equals)
<br/>
<br/>

---
# Object 클래스
자바의 모든 클래스는 Object를 상속받는다. 즉 Object는 모든 클래스의 부모이다.

Java의 모든 객체는 Object 타입으로 업캐스팅해서 관리가 가능하다.

<br/>

## <span style="color:#da7c7c">Object class의 매서드</span>
다음은 Object의 메서드들이며 자식 클래스에서 편의에 맞게 재정의해서 사용한다.
- `equals()` : 객체 를 위해 재정의한다.
- `toString()` : 객체의 설명을**내부의 값 비교** 위해 재정의한다.
- `hashCode()` : 객체 내부 값으로 **객체를 식별(같은 객체인지 식별)**하기 위해 재정의한다.

## <span style="color:#da7c7c">hashCode()와 equals()</span>
- **equals()**
    - **동등성**을 확인하는 메소드이다.
        - 동등성 : 두 개의 객체가 같은 정보를 갖고 있는 경우를 의미한다.

- **hashCode()**
    - **동일성**을 확인하는 메소드이다.
        - 동일성 : 두 개의 객체가 완전히 같은 경우를 의미한다.


Set에서는 중복되는 값을 넣을 수 없기 때문에 새로운 값을 넣을 때 hashCode()를 통해 동일한 객체인지 확인한다.

만약 hash code가 동일한 객체가 존재한다면 equals를 통해 동등성을 확인한 후 Set에 넣거나 넣지 않는다.

특정 조건에서 Set에 객체를 추가하고 싶을 경우 객체의 hashCode()와 equals()를 재정의해서 사용하면 된다.

**equals()를 재정의하는 경우 hashCode() 역시 객체 자체의 값을 반환하도록 재정의해야 한다.**