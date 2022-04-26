---
layout: post
title:  "[JAVA] Thread"
categories: tech
tags: java
comments: true
---
**Contents**
- [Thread란?](#thread란)
- [실행 메서드](#실행-method)
- [Deamon 스레드란?](#demon-thread)
- [스레드의 우선순위](#thread-priority스레드-우선순위)
<br/>
<br/>

---
# Thread란?
하나의 프로세스 내부에서 독립적으로 실행되는 하나의 작업 단위를 말한다.

세부적으로는 OS에 의해 관리되는 하나의 작업 혹은 태스크를 의미한다.

`Thread` class를 상속받거나 `Runnable` interface를 구현해서 스레드 클래스를 정의할 수 있다.

Runnable interface를 구현할 경우엔 Thread를 상속받지 않았기 때문에 thread 객체를 생성할 때 매개변수로 넣어주면 된다.

스레드와 태스크, 작업은 바꿔서 사용해도 무관하다.

CPU가 싱글 코어일 때와 듀얼 코어일 때 멀티 스레드가 다르게 실행된다.

싱글 코어라면 여러 스레드가 하나씩 돌아가면서 실행되고 듀얼 코어라면 여러 스레드가 두 개씩 돌아가면서 실행된다.

부모 스레드, 자식 스레드

### 실행 method
- `@Override run()`
    - 싱글 스레드로 사용할 때 호출하며 thread가 생성되지 않고 run() 메서드만 실행된다.
- `@Override start()` 
    - 새로운 스레드를 생성하며 해당 스레드가 실행되면 run() 메서드가 실행된다.
    - 멀티 스레드로 동작한다.


### Demon thread
부모 스레드가 죽었을 때 자식 스레드를 어떻게 할지 정해야 한다.

`isDemon()`을 통해 부모 스레드가 살아있는지 확인할 수 있다.

`setDemon()` 메서드를 통해 부모가 종료되면 자식도 종료되게 설정할 수 있다. 

### thread priority(스레드 우선순위)
`.getPriority()`를 통해 해당 스레드의 우선순위를 확인할 수 있다.

우선 순위의 기본 값은 5이며 1 ~ 10으로 값이 존재한다.

우선 순위가 클 수록 순위가 높으며 10이 제일 먼저 실행된다.
