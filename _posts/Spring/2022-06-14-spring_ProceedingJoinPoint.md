---
layout: post
title:  "[Spring] ProceedingJoinPoint"
categories: tech
tags: spring
comments: true
---
# ProceedingJoinPoint
일반적인 경우 Around Advice에서 사용할 공통 기능의 메서드는 대부분 파라미터로 전달받은 ProceedingJoinPoint의 `proceed()` 메서드만 호출하여 구현한다.

그런데 어떤 상황에서는 대상 객체에 대한 정보와 실행되는 메서드의 정보, 그리고 메서드를 호출할 때 전달된 인자에 대한 정보를 필요로 할 경우가 있다.

ProceedingJoinPoint 인터페이스는 다음과 같은 기능을 제공한다.

- `Signature getSignature()`
    - 호출되는 메서드의 정보를 구하는 메서드
    - `String getName()`
        - 메서드의 이름을 제공한다.
    - `String toLongString()`
        - 메서드를 완전히 표현한 문장을 구한다.
    - `String toShortString()`
        - 메서드를 축약하여 표현한 문장을 구한다.
- `Object getTarget()`
    - 대상 객체를 구하는 메서드
- `Object[] getArgs()` 
    - 파라미터 목록을 구하는 메서드