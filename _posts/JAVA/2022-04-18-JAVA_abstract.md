---
layout: post
title:  "[JAVA] 추상화(Abstraction)"
subtitle: 객체지향 프로그램의 추상화
categories: tech
tags: java
comments: true
---
**Contents**
- 추상화
    - [abstract](#추상화-abstraction)
    - [interface](#interface)
        - [상속 키워드](#interface-상속)
        - [인터페이스 구현](#interface-구현)
<br/>
<br/>

---
# 추상화 Abstraction
목적과 관련이 없는 것을 제거하고 필수적인 요소만을 표현해 둔 것을 말한다.

클래스와 메서드 앞에 `abstract`를 붙여 생성한다.

클래스는 객체를 생성할 수 있지만 추상 클래스는 객체를 생성할 수 없다.

<br/>

동물 추상 클래스로 예시를 들어보자. 

<u>동물</u>은 <u>포유류, 조류, 어류</u> 등 다양하게 존재하며 <u>모든 동물은 움직임과 울음의 특징</u>을 갖고 있으며 다음과 같이 정의할 수 있다.

```java
// 추상 클래스
public abstract class 동물 {
    // 추상 메서드
	abstract void 움직임();
	abstract void 울음();
    abstract void 호흡();
    void 동물만의특징() {};
}
```
<br/>

이제 동물 추상 클래스를 상속받는 포유류 클래스를 생성해보자.

`extends`로만 추상 클래스를 상속받으면 compile error가 발생한다. 이는 추상 클래스 안의 추상 메서드를 정의하지 않아서 발생한다.

```java
public class 포유류 extends 동물 {
    // compile error
    // The type 포유류 must implement the inherited abstract method 동물.움직임()
}
```
<br/>

이를 해결하는 방법은 다음과 같다.
1. 추상 클래스의 **모든 추상 메서드를 오버라이딩** 한다.  
    ```java
    public class 포유류 extends 동물 {
        @Override
        void 움직임() {
            System.out.println("포유류의 움직임");
        }
        @Override
        void 울음() {
            System.out.println("포유류의 울음");
        }
    }
    ```
2. 포유류 클래스도 추상 클래스로 정의한다.  
    ```java
    public abstract class 포유류 extends 동물 {
        void 포유류특징() {};

        @Override
        void 호흡(){
            System.out.println("폐호흡");
        }
    }
    ```
    - 포유류도 개, 고양이, 사자 등으로 분류할 수 있으니 추상 클래스로 생성할 수 있다.

<br/>
2번 방법을 선택한 후 포유류를 상속받는 개 클래스를 정의해보자

```java
public class 개 extends 포유류 {
	@Override
	void 움직임() {
		System.out.println("개같이 걷기");
	}

	@Override
	void 울음() {
		System.out.println("개같이 울기");
	}
}
```
<br/>

동물 클래스의 `호흡()` 추상 메서드는 포유류 추상 클래스에서 재정의했기 때문에 포유류를 상속받는 개 클래스에서 재정의하지 않아도 된다.

고양이 클래스도 포유류 클래스를 상속받아서 만든 후 개와 고양이 객체를 만든다면 동물과 포유류 자료형으로 객체를 관리할 수 있다.
```java
고양이 cat = new 고양이();
개 dog = new 개();

동물[] animal = new 동물[] {dog, cat};
포유류[] mammalia = new 포유류[] {dog, cat}
```
개, 고양이 클래스는 포유류 클래스를 상속받았고 포유류 클래스는 동물 클래스를 상속받아서 가능하다.

<br/>
<br/>
<hr>

# interface
완전한 추상 클래스이다.

java에서는 다중 상속이 불가능하지만 interface는 다중 상속을 할 수 있다.

interface를 통해 관계가 없는 클래스들에 연관성을 부여할 수 있다.

정의된 메서드를 가질 수 없어서 모든 메서드는 추상 메서드로 정의해야 한다.

interface를 상속받는 클래스는 **interface의 모든 추상 메서드를 재정의**해야 한다.

`interface` 키워드를 통해 선언할 수 있으며 `implements` 키워드를 통해 상속받을 수 있다. 

또한, v1.8이전에는 상수, 추상 메서드 선언만 가능했지만 이후 버전에서는 default, static 메서드가 추가되었다.
- default method
    - interface를 상속받는 모든 클래스에 재정의하지 않아도 사용이 가능한 메서드
    - 필요에 의해 재정의할 수 있다.
- static method
    - interface의 정적 메서드도 클래스의 정적 메서드와 똑같은 방식으로 사용이 가능하다.

<br/>
<br/>

## <span style="color:#da7c7c">interface 상속</span>
- `interface`를 상속받아 `interface`를 생성하기
    - `extends` 키워드 사용
- `interface`를 상속받아 `class` 생성하기
    - `implements` 키워드 사용  
    ```java
    public class 고래 extends 포유류 implements 물에서사는생물 {
        @Override
        void 움직인다() {
            System.out.println("고래같이 움직인다.");
        }
    }
    ```

<br/>
<br/>

## <span style="color:#da7c7c">interface 구현</span>
```java
public interface 물에서사는생물 {
    // 1) public static final이 자동으로 붙지만 생략된다.
    int a = 1;

    // 2) interface에서는 메서드를 정의할 수 없다.
    void method(){};

    // 3) public abstract가 자동으로 붙지만 생략된다.
    void 물생활();

    // 4) default 메서드
    default void methodD() {
		System.out.println("default method");
	}

    // 5) 정적 메서드
	static void methodS() {
		System.out.println("static method");
	}
}
```
1. 상수 선언 시 앞에 `public static final`이 자동으로 생성된다.
    - `int a = 1` = `public static final int a = 1`
2. interface에서 메서드는 선언만 할 수 있다. 만약 body(`{ }`)를 적을 경우 에러가 발생한다.
3. 메서드를 선언할 때 `public abstract`가 자동으로 생성된다.
4. `default` 키워드를 통해 디폴트 메서드를 생성할 수 있다.
5. `static` 키워드를 통해 정적 메서드를 생성할 수 있다.
