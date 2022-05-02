---
layout: post
title:  "[Oracle] JDBC"
categories: tech
tags: oracle
comments: true
---
**Contents**
- [JDBC란?](#jdbc)
- [연결 방법](#연결-방법)
- [쿼리 실행](#query-실행)
    1. [Statement](#1-statement)
    2. [PreparedStatement](#2-preparedstatement)
<br/>
<br/>

---
# JDBC
Java DataBase Connection

자바와 데이터베이스를 연동하는 작업을 말한다.

외부 라이브러리를 이용하기 때문에 workspace에 lib 폴더를 생성한 후 관리하면 된다.

- **lib** : 외부 라이브러리를 관리하는 폴더
- **bin** : 실행 파일을 관리하는 폴더
- **src** : 코드 파일을 관리하는 폴더

드라이버를 프로젝트 디렉토리에 복사한 후 **빌드 패스**에 추가해야 한다. (드라이버 클래스가 정상적으로 로딩되는지 확인하기)

<br/>
<br/>


## <span style="color:#da7c7c">연결 방법
다음의 형식으로 연결한다.

```java
Connection conn = null;

try {
    Class.forName("oracle.jdbc.OracleDriver");
    System.out.println("드라이버 로딩 성공");

    conn = DriverManager.getConnection(url, id, pwd);
    System.out.println("오라클 데이터베이스 접속 성공!");
} catch (ClassNotFoundException e) {
    // 라이브러리가 추가되지 않은 상태면 에러가 발생
    e.printStackTrace();
} catch (SQLException e) {
    e.printStackTrace();
}
```
1. Connection interface를 생성
2. 드라이버 로딩
3. 오라클 데이터베이스 접속한 후 Connection 객체에 대입
    - `DriverManager.getConnection()`의 매개변수로 url와 접속할 계정의 id, 비밀번호를 전달한다.

<br/>
<br/>
<br/>

## <span style="color:#da7c7c">Query 실행
Java와 DB가 연결에 성공하였으면 다음의 객체를 통해 Query를 실행할 수 있다.

### 1. Statement
사용자의 개입이 없이 Query를 실행할 경우 사용한다.

```java
import java.sql.Statement;

...

Statement stmt = null; // 쿼리 전송 결과 가져오기

stmt = conn.createStatement();

// insert into "INFO" values (101, '홍길동', 'AB');
String name = "'홍길동'";
String bloodType = "'AB'";
String sql = "insert into \"INFO\" values (101, " + name + ", '1444-01-01', " + bloodType + ")";
```
- 실행할 sql을 String 변수로 분리해서 만들어 놓는다.

- `stmt.executeUpdate(sql)` : insert, delete와 같은 명령을 실행할 경우 사용
    ```java
    int result = stmt.executeUpdate(sql); 
    ```  
    update된 행의 개수를 반환한다.
- `stmt.executeQuery(sql)` : select 명령을 실행할 경우 사용
    ```java
    import java.sql.ResultSet;
    ...
    ResultSet rs = null;
    String sql = "select \"NUMBER\", \"NAME\" as \"NICKNAME\", \"BLOOD_TYPE\" from \"INFO\"";
    rs = stmt.executeQuery(sql); // 쿼리 전송!
    while (rs.next()) {
        System.out.print(rs.getLong(1) + ",");
        System.out.println(rs.getString("NICKNAME") + ", ");
        System.out.println(rs.getString(3));
    }
    ```
    - `ResultSet`으로 select 문의 결과를 받는다.
    - `ResultSet`을 출력할 때는 index로 접근도 가능하며 column명으로도 접근이 가능하다.(`get자료형()`은 필수)

<br/>
<br/>

### 2. PreparedStatement
사용자가 입력한 값을 사용하여 쿼리를 실행할 경우 Statement를 사용하면 **SQL Injection**이 발생할 위험이 있다.
- SQL Injection : 악의적인 사용자가 보안상의 취약점을 이용하여, 임의의 SQL문을 주입하고 실행되게 하여 데이터베이스가 비정상적인 동작을 하도록 조작하는 행위


```java
import java.sql.PreparedStatement;

...

PreparedStatement pstmt = null; 

String name = "홍길동";
String bloodType = "AB";
String sqlD = "delete from \"INFO\" where \"NAME\" = ? and \"BLOOD_TYPE\" = ?";

pstmt = conn.prepareStatement(sqlD);
pstmt.setString(1, name);
pstmt.setString(2, bloodType);

int result = pstmt.executeUpdate();
```
1. SQL 쿼리 템플릿을 생성할 `PreparedStatement`객체를 생성한다.
2. SQL문 String 자료형 생성
    - 사용자에게 입력받은 자리는 `?`를 넣는다.
3. `prepareStatement(sql)`를 통해 해당 SQL문의 템플릿을 준비한다.
4. 사용자에게 값을 입력받아 `?`를 채워넣는다.
    - `pstmt.setString(index, value)` 메서드를 통해 값을 넣을 `?`의 인덱스와 입력받은 값을 매개변수로 전달한다.
    - 인덱스는 1부터 시작한다.
5. SQL 문이 정상적으로 실행되면 update된 행의 길이나 select된 행을 반환한다.   
