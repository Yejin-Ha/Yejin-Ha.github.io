---
layout: post
title:  "[Spring] Auto DI 의존자동주입"
categories: tech
tags: spring
comments: true
---
# 의존자동주입 Auto DI
어노테이션을 사용한 의존 자동 주입에 대해 정리한다.

의존자동주입에는 2가지 방법이 있다.
1. @Autowired
2. @Resource
<br/>
<br/>

## 1. `@Autowired`
- 생성자, 필드, 메서드, 매개변수에 적용하면 해당 타입에 할당할 수 있는 bean 객체를 찾아서 주입대상으로 자동 지정한다.  
    ```xml
    <!-- appCtx.xml -->
    <context:annotation-config />
	<bean id="memberDao" class="examspring02.MemberDao"></bean>
    ```
    ```java
    // MemberRegisterService.java
    @Autowired
	public MemberRegisterService(MemberDao memberdao) {
		this.memberDao = memberdao;
	}
    ```
<br/>
<br/>

- 동일한 타입을 가진 bean 객체가 여러개 존재한다면 `qualifier`와 `@Qualifier(value)`를 통해 bean 객체를 지정할 수 있다.
    ```xml
    <!-- appCtx.xml -->
    <context:annotation-config />
	<bean id="dao1" class="examspring02.MemberDao">
        <qualifier value="daoA" />
    </bean>
	<bean id="dao2" class="examspring02.MemberDao">
        <qualifier value="daoB" />
    </bean>
    ```
    ```java
    // MemberRegisterService.java
    // daoB bean 객체를 지정해서 사용
    @Autowired
    @Qualifier("daoB")
	public MemberRegisterService(MemberDao memberdao) {
		this.memberDao = memberdao;
	}
    ```
<br/>
<br/>

- **`@Autowired` 어노테이션 적용 순서**
    1. 타입이 같은 bean 객체를 검색
        - bean 객체가 1개면 그 객체를 사용
        - bean 객체가 2개 이상 존재
            1. `@Qualifier`로 지정한 bean 객체를 찾아 주입
            2. `@Qualifier`로 지정한 bean 객체가 없다면 이름이 같은 bean 객체를 찾아 주입
    2. 매칭되는 bean 객체를 찾지 못할 경우 스프링은 예외를 발생시킨다.
        - `required=false`를 지정하면 예외가 발생하지 않는다.
<br/>
<hr>
<br/>

## 2. `@Resource` 
- Resource 어노테이션은 bean의 이름을 검색하여 자동 주입 동작한다.
    - 자동 주입 대상에 `@Resource` 어노테이션을 사용한다.
    - xml에 `<contextannotation-config />` 태그를 추가해야 된다.
    ```xml
    <!-- appCtx.xml -->
    <context:annotation-config />
	<bean id="dao" class="examspring02.MemberDao">
    </bean>
    ```
    ```java
    // MemberRegisterService.java
    @Resource(name="dao")
	public MemberRegisterService(MemberDao memberdao) {
		this.memberDao = memberdao;
	}
    ```
<br/>
<br/>

- 생성자에는 적용할 수 없다.



