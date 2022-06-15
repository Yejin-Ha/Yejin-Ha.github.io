---
layout: post
title:  "[Spring] ProceedingJoinPoint"
categories: tech
tags: spring
comments: true
---

dao는 datasource를 의존주입받는 객체이다.

-> xml에서 bean으로 설정해야된다.

쿼리 실행 결과가 2개 이상의 행일 경우 `jdbcT.query(a, b, c, d, ...)`를 통해 query문 실행 가능
- a - 실행할 쿼리
- b - 쿼리 실행 결과를 저장할 타입(dto라던가 자료형이던가)
    - `RowMapper` interface를 활용한다.
    - 해당 코드가 반복적으로 사용되면 `RowMapper`를 상속받는 클래스로 대체할 수 있다.
- c, d, ... - set할 값이 있으면 이걸 사용. 없으면 안써도 된ㄷㅏ


쿼리 실행 결과가 1행인 경우 `jdbcT.queryForObject()`를 통해 쿼리문 실행 가능
- 주의 사항
    1. 쿼리 실행 결과는 1행일 때만 사용 가능
    2. 쿼리 실행 결과가 1개가 아니면 `IncorrectResultSizeDataAccessException` 발생


`insert, update, delete` 쿼리를 실행할 때는 `update()` 메서드를 사용한다.
- 쿼리 실행 결과로 변경된 행의 개수를 반환한다.
