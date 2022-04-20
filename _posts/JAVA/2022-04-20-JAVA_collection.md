---
layout: post
title:  "[JAVA] Collection"
subtitle: java Collection 정리
categories: tech
tags: java
comments: true
mathjax: true
---
**Contents**
- [Collection이란?](#collection)
<br/>
<br/>

---
# Collection
**Collection**이란 데이터를 수집하기 위한 집합이다.

**Collection Framework** : **데이터를 수집하여 저장**하기 위해 사용할 수 있도록 정의해 놓은 클래스 집합
<table>
    <tr>
        <th>Set</th>
        <td>HashSet <br/>
            TreeSet
        </td>
        <td>비순차적 저장, 데이터 중복 불가능</td>
        <td></td>
    </tr>
    <tr>
        <th>Map</th>
        <td>HashMap<br/> 
            TreeMap<br/>
            Hashtable    
        </td>
        <td>비순차적 저장, 데이터 중복 가능</td>
        <td>- key, value를 함께 입려해야 한다. <br/>
            - key만 알면 value에 바로 접근이 가능함
        </td>
    </tr>
    <tr>
        <th>List</th>
        <td>LinkedList <br/> 
            Vector<br/> 
            ArrayList
        </td>
        <td>순차적 저장, 데이터 중복 가능</td>
        <td></td>
    </tr>
</table>
- HASH를 사용하면 속도가 가장 빠른 Collection을 사용할 수 있다.


