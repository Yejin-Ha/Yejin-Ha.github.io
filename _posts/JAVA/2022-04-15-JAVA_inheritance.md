---
layout: post
title:  "[JAVA] 상속(Inheritance)이란?"
subtitle: 클래스 상속
categories: tech
tags: java
comments: true
---
**Contents**
- [상속이란?](#상속-inheritance-이란)
    - 상속의 예시
- [super와 super()란?](#super와-super)
- [instanceof 메서드](#instanceof-연산자)
<br/>
<br/>

---
# 상속 Inheritance 이란?
이전에 만들어 놓은 설계도에 기능을 추가하는 것을 말한다. **코드의 재사용성 및 신뢰성이 증가**하는 특징이 있다.

`extends` 키워드를 통해 클래스 상속을 받는다.

java에서는 다중 상속을 지원하지 않는다. (다중 상속 = 여러 클래스를 상속받는 행위)

`A → A1 → A2 → A3 → A4` 이런 순서로 상속을 받는 경우엔(`A1 extends A`) A4의 부모 클래스는 A, A1, A2, A3 클래스 전부이다.

```java
// 불가능!!!
public class A extends A1, A2 {}
```

<br/>

## <span style="color:#da7c7c">상속 예시</span>
### 1. 부모 클래스
```java
public class Parents {
    int a = 100;
    void methodP() {
        System.out.println("parent method");
    }
}
```
<br/>

### 2. 부모 클래스를 상속받는 자식 클래스
```java
public class Child extends Parents {
    int a = 1;
    // 어노테이션
    @Override
    void methodP() {
        System.out.println("child method");
    }
}
```
- 자식 클래스에서는 자신만의 메서드를 작성할 수 있고 부모 클래스의 메서드를 오버라이드(**Override**)할 수 있다.
- 오버라이딩할 경우 **어노테이션**을 달아주자.(ex. `@Override`)
    - 부모/조상 클래스로부터 상속받은 메소드의 내용을 자식 클래스에 맞게 수정하는 것을 **오버라이딩**이라고 한다.
    - **Annotation** : JVM에게 알려주는 주석 역할. 컴파일할 때 확인하는 용도

<br/>
        
### 3. 자식 클래스 객체 생성 & 실행
```java
public static void main(String[] args) {
    Child ch = new Child();
    ch.methodP();
}

// 실행 결과 ===========
// child method
```
<br/>
<br/>
<hr>

# super와 super()
## <span style="color:#da7c7c">super</span>
자식 클래스가 부모 클래스로부터 상속받은 멤버를 참조할 때 사용하는 참조 변수이다. 

부모 클래스의 멤버를 참조할 때는 `super`를 자신의 멤버를 참조할 때는 `this`를 사용하여 구분한다.

```java
public class Child extends Parents {
    int a = 1;

    void methodC() {
        System.out.println(super.a);
        System.out.println(this.a);
    }
}

public static void main(String[] args) {
    Child ch = new Child();
    ch.methodC();
}

// 실행 결과 ===========
// 100
// 1
```
<br>

## <span style="color:#da7c7c">super()</span>
부모 클래스의 생성자를 호출하는 메서드이다. 

매개변수를 지정하지 않으면 디폴트 생성자가 호출되며 매개변수를 지정하면 해당 변수를 인수로 받는 생성자를 호출한다.

**반드시 첫 번째 문장에 사용되어야 한다.**

```java
class Parent {
    int p;

    Parent(int n) {
        p = n;
    }
    Parent() {
        p = 100;
    }
}

class Child extends Parent {
    Child() {
        super(9999);
    }
}
```

자식 클래스의 디폴트 생성자에는 `super()`가 디폴트로 생략되어 있으며 부모의 디폴트 생성자가 아닌 다른 생성자를 호출할 때만 사용하면 된다.

<br/>
<br/>
<hr>

# 상속에서 자주 사용되는 키워드
## <span style="color:#da7c7c">instanceof 연산자</span>
객체 타입을 확인하는 연산자이다.

주로 상속 관계에서 부모 객체인지 자식 객체인지 확인하는데 사용된다.

`객체 instanceof 클래스` 형태로 사용되며 형변환 가능여부를 확인하여 true / false 로 결과를 반환한다.

```java
class Child extends Parent{}

Parent p = new Parent();
Child ch = new Child();

// instanceof 메서드 활용 =======

p instanceof Parent; // true
ch instanceof Parent; // true
p instanceof Child; // false
ch instanceof Child; // true
```
