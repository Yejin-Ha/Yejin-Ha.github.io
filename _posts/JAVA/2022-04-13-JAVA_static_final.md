---
layout: post
title:  "[JAVA] static, final 차이"
subtitle: static과 final 키워드의 개념과 차이를 정리
categories: tech
tags: java
comments: true
---
**Contents**
- [static 멤버](#static)
    - [static 변수](#static-변수)
    - [static 메소드](#static-메서드)
- [final 키워드](#final)
    - [final 클래스](#final-클래스)
    - [final 메소드](#final-메소드)
    - [final 필드](#final-필드)
<br/>
<br/>

---
# static
멤버를 선언할 때는 **인스턴스 멤버**와 **클래스 멤버**로 선언할 수 있다.
- **인스턴스 멤버** : 객체가 만들어져야 생기는 멤버들
    - 객체(인스턴스)가 생성되면 객체마다 자동으로 생성되는 멤버
    - 객체마다 개별적으로 가져되는 속성일 때 선언한다.
- **클래스 멤버 = static 멤버** : 인스턴스와 상관없이 사용이 가능한 멤버
    - 클래스가 로딩되면 자동으로 생성된다.
    - 각 객체마다 존재할 필요가 없고 모든 객체가 하나의 공통된 속성을 가질 경우에 선언한다.
    - 객체를 생성하지 않아도 클래스명으로 바로 사용이 가능하다.
<br/>
<br/>

### <span style="color:#da7c7c">static 변수</span>
`static` 키워드를 통해 생성한 변수는 기울어져서 표기된다.

인스턴스 변수는 모든 인스턴스마다 존재하기 때문에 `this`를 통해 구별이 가능하다. 

클래스 멤버는 한 클래스에 하나만 존재하기 때문에 `this`로 구분하지 않는다.  
하지만 클래스 멤버에 `this`를 사용해도 에러가 발생하지 않는다.

```java
class Ex {
    int a; // 인스턴트 변수
    static int b; // 클래스 변수

    void print(){
        System.out.println("a: " + this.a + ", b: " + b);
        // this.b로 사용해도 에러가 발생하지 않음
    }
}

System.out.println(Ex.b); // 객체를 생성하지 않아도 객체로 바로 접근이 가능
```

<br/>

### <span style="color:#da7c7c">static 메서드</span>
클래스만 로딩된 상태에는 인스턴스 멤버가 존재하지 않기 때문에 static 멤버가 인스턴스 멤버에 접근할 경우 에러가 발생한다.

인스턴스 멤버와 클래스 멤버는 메모리에서 사용 가능한 시점이 다르기 때문에 함께 사용이 불가능하다.

**(인스턴스 멤버가 선언되기 전에는) static 메서드는 오직 static 멤버만 접근할 수 있다.**

```java
class Test {
    int a;
    static int b;

    static int getB() {
        return Test.b;
    }

    // 인스턴스 변수가 존재하기 때문에 에러가 발생한다.
    static int getAB() {
        return a + b;
    }
}

```

<br/>
<br/>
<hr>

# final

`final` 키워드는 클래스, 메소드, 필드에 붙일 수 있다.
- `final 클래스` : 상속이 불가능한 클래스
- `final 메소드` : 재정의(오버라이딩)가 불가능한 메소드
- `final 필드` : 상수 선언
<br/>
<br/>

### <span style="color:#da7c7c">final 클래스</span>
final로 선언된 클래스는 상속이 불가능하다.

```java
final class A { ... }

class ASub extends A { ... }
```

위와 같이 작성할 경우 에러가 발생하면 다음과 같은 문구가 나온다.
```
The type ASub cannot subclass the final class A
```

<br/>

### <span style="color:#da7c7c">final 메소드</span>
```java
class B {
    final void method() {
        System.out.println("hi");
    }
}

class BSub extends B {
    void method() {
        System.out.println("bye");
    }
}
```
B 클래스를 상속받는 BSub 클래스를 생성한 뒤 B 클래스에 method 메소드를 오버라이딩을 오버라이딩 해보았다.

하지만 method 메소드는 final로 선언되었기 때문에 재정의가 불가능하기 때문에 에러가 발생한다.
<br/>
<br/>

### <span style="color:#da7c7c">final 필드</span>
필드를 final로 선언하면 상수가 된다.

```java
class C {
    final int A = 2;    
}
```
