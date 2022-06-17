---
layout: post
title:  "[Spring] MessageSource"
categories: tech
tags: spring
comments: true
---
# MessageSource
"이메일" 같이 여러 페이지에의 폼에서 반복적으로 사용되는 문자열이 존재한다고 가정하자.

문자열을 "email"로 변경해야 할 경우 모든 폼에서 동일하게 수정해야하는 번거로움이 있다.

이런 상황을 효율적으로 해결하기 위해 MessageSource를 사용한다.
<br/>
<br/>

### step 1. properties 파일 생성
`src/main/resources`에 message 폴더를 만든 후 `label.properties`를 다음과 같이 생성한다.

```properties
member.register=회원가입
next.btn=다음단계
member.info=회원정보
email=이메일
name=이름
password=비밀번호
password.confirm=비밀번호 확인
register.btn=가입 완료
register.done=<strong>{0} {1}님</strong> 회원 가입을 축하합니다.
``` 
- `key=value` 형식으로 입력한다.
- `register.done`
    - MessageSource의 `getMessage()`가 자동으로 적용된다.
    - {0}은 전달받은 argument의 첫 번째(0) 요소를 바인딩할 자리이다.
<br/>
<br/>

### step 2. messageSource bean 객체 생성
기전에 mvc 객체를 생성한 xml파일에 아래의 내용을 추가한다.
```xml
<bean id="messageSource"
    class="org.springframework.context.support.ResourceBundleMessageSource">
    <property name="basenames">
        <list>
            <value>message.label</value>
        </list>
    </property>
    <property name="defaultEncoding" value="UTF-8" />
</bean>
```
- bean의 id는 무조건 `messageSource`로 해야한다.
- list의 value를 통해 properties의 경로를 지정한다.
    - message.label = message/label.properties
- 여러 설정파일을 등록할 경우 `<value>` 태그를 추가하면 된다.
<br/>
<br/>

### step 3. 적용하기
```html
<!-- 상단에 추가 -->
<%@ taglib prefix="spring" uri="http://www.springframework.org/tags"%>

...

<spring:message code="register.done" arguments="${formData.name }" />
```
- MessageSource를 사용할 부분에 `<spring:message>` 태그를 사용한다.
- code : MessageSource에 입력한 key를 입력한다.
- arguments : messageSource에 전달할 arguments를 입력한다.
    - 하나만 입력할 경우 -> `arguments="hi"`
    - 여러개 입력할 경우 -> `arguments="hi, bye, seeyou"`
