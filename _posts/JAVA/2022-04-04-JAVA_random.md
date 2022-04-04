---
layout: post
title:  "[JAVA]난수 생성하기"
subtitle: 난수를 생성하는 방법
categories: tech
tags: java
comments: true
---
**Contents**
1. [Random 클래스 활용](#1-random-클래스-활용)
2. [Math.random](#2-mathrandom)

<br/>
<br/>

---
# JAVA 난수 생성하기
## <span style="color:#da7c7c">1. Random 클래스 활용</span>
```java
import java.util.Random;
public class Ex {
    public static void main(String[] args) {
        // 랜덤 객체 생성
        Random ran = new Random();

        // ran.next자료형 : 해당 자료형에 맞는 난수를 생성
        int a = ran.nextInt(); // int형 난수 1개 생성
        int b = ran.nextInt(30); // 0 ~ 29에서 int형 난수 1개 생성
    }
}
```
- java.util 패키지 안에 있는 Random class를 불러와서 사용한다.
- `new`를 통해 객체를 생성해야 한다.

<br/>
<br/>

## <span style="color:#da7c7c">2. Math.random()</span>

