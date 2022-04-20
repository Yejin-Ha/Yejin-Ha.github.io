---
layout: post
title:  "[JAVA] 제네릭(Generic)"
subtitle: Generic에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**
- [제네릭이란?](#generic-제네릭)
- [제네릭의 장점](#generic의-장점)
- [제네릭 사용 방법](#사용방법)
<br/>
<br/>

---
# Generic 제네릭
데이터 형식에 의존하지 않고, 하나의 값이 여러 다른 데이터 타입들을 가질 수 있도록 하는 방법이다.

제네릭은 클래스 내부에서 지정하는 것이 아니라 외부에서 사용자에 의해 지정되는 것을 의미한다.

<br/>

## <span style="color:#da7c7c">Generic의 장점</span>
1. 잘못된 타입이 들어올 수 있는 것을 컴파일 단계에서 방지할 수 있다.
2. 클래스 외부에서 타입을 지정하기 때문에 타입을 체크하고 변환해줄 필요가 없다.(관리가 편함)
3. 비슷한 기능을 지원하는 경우 코드의 재사용성이 높아진다.

<br/>
<br/>

## <span style="color:#da7c7c">사용방법</span>
`< >` : 다이아몬드 연산자라고 부르며 C++의 템플릿과 동일한 역할을 한다.

|타입|설명|
|:---:|:---:|
|```<T>```|Type|
|```<E>```|Element|
|```<K>```|Key|
|```<V>```|Value|
|```<N>```|Number|
