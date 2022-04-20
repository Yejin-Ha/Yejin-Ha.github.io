---
layout: post
title:  "[JAVA] 래퍼(Wrapper) 클래스"
subtitle: java의 래퍼 클래스에 대한 정리
categories: tech
tags: java
comments: true
mathjax: true
---
**Contents**
- [wrapper class란?](#wrapper-class)
- [Boxing과 Unboxing](#boxing--unboxing)
- [Auto-Boxing과 Auto-Unboxing](#auto-boxing--auto-unboxing)
<br/>
<br/>

---
# Wrapper Class
기본 자료타입(primitive type)을 객체로 다루기 위해 사용하는 클래스를 래퍼클래스(wrapper class)라고 한다.

|기본 타입 Primitive type|래퍼 클래스 wrapper class|
|:---:|:---:|
|byte|Byte|
|char|Character|
|int|Integer|
|float|Float|
|double|Double|
|long|Long|
|short|Short|

<br/>

## <span style="color:#da7c7c">Boxing & Unboxing</span>
- Boxing : 기본 타입의 값을 래퍼 클래스 객체로 만드는 과정
- Unboxing : 래퍼 클래스 객체를 기본 타입의 값으로 만드는 과정(Boxing의 반대)

<br/>
<br/>

## <span style="color:#da7c7c">Auto-Boxing & Auto-Unboxing</span>
직접 박싱, 언박싱하지 않아도 자동으로 박싱, 언박싱이 일어나는 경우가 있다.

래퍼 클래스 타입에 기본 자료형이 대입되는 경우 자동 박싱이 이루어진다.(자동 언박싱은 반대의 경우)
