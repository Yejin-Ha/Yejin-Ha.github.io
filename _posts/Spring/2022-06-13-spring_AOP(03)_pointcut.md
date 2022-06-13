---
layout: post
title:  "[Spring] AOP(03) - PointCut"
categories: tech
tags: spring
comments: true
---
# AOP - PointCut
JoinPoint를 지정하는 표현식

반복되는 execution() 메서드를 PointCut을 통해 지정하여 편리하게 사용이 가능하다.

## PointCut 생성 방법
**1. 어노테이션 사용**
```java
public class CommonPointCut {
    @Pointcut("execution(* usingComputer(..))")
    public void myPointCut() {}
}
```
- 앞서 작성한 코드에서 반복해서 사용되는 `"execution(* usingComputer(..))"` 을 `myPointCut()` 메서드를 대신하여 사용한다.

<br/>

- 기존 코드
    ```java
	@Before("execution(public int aop02.*.usingComputer(String))")
    public void bootingAndLogin(JoinPoint jp) {
        String pwd = (String) jp.getArgs()[0];
        System.out.println("컴퓨터 부팅 시작. " + pwd + " 입력 로그인");
    }
	```
- Pointcut을 활용한 코드
    ```java
	@Before("CommonPointCut.myPointCut()")
    public void bootingAndLogin(JoinPoint jp) {
        String pwd = (String) jp.getArgs()[0];
        System.out.println("컴퓨터 부팅 시작. " + pwd + " 입력 로그인");
    }
	```

<br/>

**2. xml 사용**
```xml
<aop:config>
    <aop:pointcut expression="execution(* usingComputer(..))" id="myPoinCut" />
    <aop:aspect ref="myAspect">
        <aop:before method="bootingAndLogin" pointcut-ref="myPoinCut" />
    </aop:aspect>
</aop:config>
```
- `myPointCut`이라는 id로 PointCut을 생성한다.
- PointCut을 활용하는 aspect는 `pointcut-ref`를 통해 설정할 수 있다.
