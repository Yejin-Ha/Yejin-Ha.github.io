---
layout: post
title:  "[JAVA]연산자"
subtitle: JAVA의 연산자에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**
- [연산자란?](#연산자)
- [자주 사용되는 연산자](#자주-사용되는-연산자)
- [특이 사항](#특이-사항)

<br/>
<br/>

---
# <span style="color:#da7c7c">연산자</span>
- 데이터를 가공하기 위해 사용하는 기호 집합
- 기존 데이터에서 연산자를 통해 원하는 값을 얻기 위해 사용한다.
- 특정 연산자를 제외하고는 왼쪽에서 오른쪽으로 연산을 진행한다.
- **우선 순위**
    > 증감 연산자  ->  산술 연산자  ->  대입 연산자  ->  비교 연산자  ->  논리 연산자  ->  단항 연산자

<br/>
<br/>

## <span style="color:#da7c7c">자주 사용되는 연산자</span>
<table>
<tr>
    <th>최우선 연산자</th>
    <td><code>.</code> - 멤버 연산자</td>
</tr>
<tr>
    <th>산술 연산자</th>
    <td><code>/</code> - 몫을 구함<br/><code>%</code> - 나머지 연산자(mod 연산)</td>
</tr>
<tr>
    <th>관계 연산자</th>
    <td>결과가 boolean 타입으로 반환된다.</td>
</tr>
<tr>
    <th>논리 연산자</th>
    <td><code>&&</code> - <B>and 연산자</B>. 모든 조건이 true면 true, 하나라도 false면 false<br/><code>||</code> - <B>or 연산자</B>. 하나라도 true면 true</td>
</tr>
<tr>
    <th>대입 연산자</th>
    <td><code>=</code>, <code>+=</code>, <code>*=</code>, <code>-=</code>, ...</td>
</tr>
<tr>
    <th>단항 연산자</th>
    <td><code>문자++</code>, <code>문자--</code>, <code>!</code>, <code>+/-</code></td>
</tr>
<tr>
    <th>증감 연산자</th>
    <td><code>++문자</code>, <code>--문자</code>, <code>-=</code>, ...</td>
</tr>
<tr>
    <th>삼항 연산자</th>
    <td><code>(조건항) ? (true 결과) : (false 결과)</code></td>
</tr>
<tr>
    <th>비트 연산자</th>
    <td><code>~</code> - Not 연산자<br/><code><<, >>, >>></code> - shift 연산자. bit를 화살표 방향으로 미는 것 <br/><code>&, |, ^</code> -> <code>^</code> : Xor 연산자. 같으면 false, 다으면 true 반환</td>
</tr>
</table>

<br/>
<br/>

## <span style="color:#da7c7c">특이 사항</span>
- 대입 연산자
    ```java
    byte a = 10;
    a = a + 1;
    ```
    a는 1byte인데 1은 4byte라서 연산결과는 4byte로 반환된다.  
    4byte를 1byte에 대입하려 해서 error 발생
    ```java
    byte a = 10;
    a += 1;
    ```
    하지만 대입 연산자를 사용하면 1을 a와 동일한 타입으로 형변환해서 알아서 계산해준다.

<br/>

- 증감 연산자
    ```java
    int a = 10;
    int b = a++; // 단항 연산자
    int c = ++a; // 증감 연산자
    
    a = 12, b = 10, c = 12
    ```
    - 증감 연산자가 대입 연산자보다 우선순위가 높다.
    - 단항 연산자가 대입 연산자보다 우선순위가 낮다.
        > 증감 연산자 -> 대입 연산자(`=`) -> 단항 연산자

<br/>

- 논리 연산자의 **short circuit evalution**
    1. 논리 연산자를 기준으로 전체를 두 개로 나눈다.
        ```java
        bo = a++ > 0 || 1 < ++b * d-- / ++c;

        1. a++ > 0 
        2. 1 < ++b * d-- / ++c
        ```
    2. 첫번째 식의 결과가 전체 결과에 영향을 준다면 최소의 행위만 하고 종료한다.
        - `&&` -> A && B 에서 A가 false면 전체 결과는 무조건 false이므로 B를 실행하지 않는다.
        - `||` -> A && B 에서 A가 true면 전체 결과는 무조건 true 이므로 B를 실행하지 않는다.

<br/>

- `~` Not 연산자
    ```java
    byte a = 10; // 00001010
    ~a;          // 11110101
    ```
<br/>

- `<<, >>, >>>` shift 연산자
    - 밀린 비트는 부호 비트로 채운다. 양수는 0, 음수는 1
    ```java
    byte a = 10; // 00001010
    a <<= 2;     // 001010_ _ -> 00101000 
    // a는 40

    byte b = -1; // 11111111
    b >>= 2;     // _ _ 111111 -> 11111111
    // b는 -1
    ```
<br/>

- `&, |, ^` 연산자
    ```java
    byte a = 10;
    a = a & 3; 
    // 10 = 00001010
    // 3  = 00000011
    //   => 00000010
    a = 2
    ```
    ```java
    byte b = 10;
    b = b | 3;
    // 10 = 00001010
    // 3  = 00000011
    //   => 00001011
    b = 11
    ```
    ```java
    byte c = 10;
    c = c ^ 3;
    // 10 = 00001010
    // 3  = 00000011
    //   => 00001001
    c = 9
    ```
<br/>

- `System.out.print`에서의 산술 연산자 `+`
    - `1+2=3`을 출력하고 싶어서 위와 같이 코드를 작성하고 실행하면 `46=2` 이 결과로 반환된다.
        ```java
        int a = 1, b = 2; char operator = +;
        int result = a + b;

        System.out.println(a + operator + b + "=" + result);
        ```
    `int`(a, b), `char`(operator)는 모두 정수형이라서 `+` 연산자를 만나면서 1 + 43(ASCIIcode값) + 2가 실행되기 때문이다.
    <br/>
    원하는 결과를 출력하기 위해서는 다음과 같이 코드를 작성하면 된다.
    <br/>
        ```java
        // 방법 1
        System.out.printf("%d %s %d = %d", a, operator, b, result);
        // 방법 2 - 연산자로 ""와 정수를 더하면 문자열이 된다.
        System.out.println("" + a + operator + b + "=" + result);
        ```
