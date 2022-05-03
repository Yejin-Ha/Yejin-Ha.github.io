---
layout: post
title:  "[Oracle] JDBC"
categories: tech
tags: oracle
comments: true
---
**Contents**
1. [DAO](#dao-data-access-object)
2. [DTO](#dto-data-transfer-object)
3. [VO](#vo-value-object)
<br/>
<br/>

---
# DAO Data Access Object
DB에 접근하기 위한 객체로 직접 DB에 접근하여 데이터를 삽입, 삭제, 조회 등 조작할 수 있는 기능을 수행한다.

로직과 비즈니스 로직을 분리하기 위해 사용되며 DB와 연결할 Connection 까지 설정되어 있는 경우가 많다.

<br/>
<br/>

# DTO Data Transfer Object
로직을 갖지 않는 순수한 데이터 객체이며 getter/setter 메서드만 가진 클래스를 의미한다.

<br/>
<br/>

# VO Value Object
DTO와 달리 Read-Only 속성ㅇ르 갖는 값 오브젝트이다.


