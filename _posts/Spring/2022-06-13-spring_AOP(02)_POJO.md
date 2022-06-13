---
layout: post
title:  "[Spring] AOP(02) - POJO"
categories: tech
tags: spring
comments: true
---
# AOP - POJO
이 포스트에선 [[Spring] AOP(01)](링크넣기) 를 POJO 방식으로 설정하는 방법을 게시한다.


**POJO** 
- Play Old Java Object
- 어떠한 객체에도 의존하지 않는 순수한 자바 객체를 의미한다.

<br/>

**MyAspect 클래스를 pojo 객체로 수정한다.**
```java
public class MyAspect {
	public void bootingAndLogin(JoinPoint jp) {
		String pwd = (String) jp.getArgs()[0];
		System.out.println("컴퓨터 부팅 시작. " + pwd + " 입력 로그인");
	}
}
```

<br/>

**after로 실행할 pojo 객체를 하나 더 만든다.**
```java
public class FinishAspect {
	public void shutdown(JoinPoint jp) {
		String com = jp.getTarget().getClass().getSimpleName();
		System.out.println(com + " 컴퓨터 종료");
  	}
}
```

<br/>

**xml을 통해 해당 객체를 aspect로 지정한다.**
```xml
<bean id="myAspect" class="aop03.MyAspect" />
<bean id="finishAspect" class="aop03.FinishAspect" />
<bean id="programmer" class="aop03.Programmer" />

<aop:config>
    <aop:aspect ref="myAspect">
        <aop:before method="bootingAndLogin"
            pointcut="execution(* usingComputer(..))" />
    </aop:aspect>
    <aop:aspect ref="finishAspect">
        <aop:after method="shutdown"
            pointcut="execution(* usingComputer(..))" />
    </aop:aspect>
</aop:config>
```
- `<aop:aspect>` - ref로 설정되는 객체를 aspect로 지정한다.
- `<aop:before>` - target 메서드가 실행되기 전에 실행한다.
    - `method` - aspect로 지정된 객체에서 target 메서드에서 실행할 메서드를 설정한다.
    - `pointcut` - target 메서드를 지정한다.

<br/>

**코드를 실행하여 결과를 확인해본다.**
```java
public class Main {
    public static void main(String[] args) {
        ClassPathXmlApplicationContext ctx = new ClassPathXmlApplicationContext("config.xml");
        
        Person p1 = ctx.getBean("programmer", Person.class);			
        int useT1 = p1.usingComputer("1234");
        System.out.println(p1.getClass().getName() + "이용시간:" + useT1);
    }
}
```
- 실행 결과
    ```
    컴퓨터 부팅 시작. 1234 입력 로그인
    [코딩을 한다.]
    Programmer 컴퓨터 종료
    com.sun.proxy.$Proxy4이용시간:200
    ```
