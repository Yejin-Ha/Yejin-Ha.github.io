---
layout: post
title:  "[JAVA] 접근제한자/접근제어자"
subtitle: java의 protected, public, private에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**  
- [접근제한자란?](#접근제한자)
- [접근제한자 키워드](#접근제한자)

<br/>
<br/>

---
# 접근제한자
자바는 캡슐화로써 외부에서 접근할 수 없도록 코드가 구성되어야 하기 때문에 접근제한자를 사용하여 내부 데이터를 관리한다.
- **접근제어자**라고도 부른다.

- 다음은 객체(클래스)의 멤버에 대한 접근을 제한하기 위한 키워드이다.

    |접근제한자|기능|
    |:---:|:---|
    |`default(package)`|접근 제어 선언이 없는 멤버. 동일 패키지까지 직접 접근이 가능하다.|
    |`protected`|`default`와 같고 상속 관계에서 직접 접근이 가능함|
    |`public`|접근에 제한이 없는 멤버|
    |`private`|클래스 내부에서만 직접 접근이 가능|
