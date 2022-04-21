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
- [ArrayList 메서드](#1-list)
- [Map](#2-map)
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

<br/>

## <span style="color:#da7c7c">1. List</span>
1. **ArrayList**
- `add(idx, val)` : index를 입력하면 해당 자리에 값을 추가하고 기존에 있는 값들을 뒤로 한 칸씩 미룬다.
    - index를 입력하지 않으면 맨 마지막에 값 추가
- `set(idx, val)` : 해당 index의 값을 val로 바꾼다.
    - 해당 index에 값이 존재하지 않으면 error 발생(`IndexOutOfBoundsException`)
- `remove(index)` : 해당 index의 값을 제거한다.
    - 제거할 값을 반환함
- `clear()` : ArrayList의 모든 값을 제거한다.(초기화)
- `contains(val)` : value가 존재하는지 확인하고 boolean 타입으로 결과를 반환해준다.
- `indexOf(val)` : value가 존재한다면 값이 존재하는 index를 반환하고 존재하지 않으면 -1을 반환한다.



## <span style="color:#da7c7c">2. Map</span>
key와 value를 mapping 시켜 데이터를 저장하는 방식이다.

제네릭(Generic)은 2개를 입력할 수 있다. `<key 자료형, value 자료형>`

순서가 존재하지 않으면 key의 중복은 허용되지 않고 value의 중복은 허용된다.

- HashMap
- TreeMap
- HashTable(자체 자동화 처리 적용)

동일한 key로 값을 넣으면 value가 대체된다.

key만 넣고싶은 경우에는 value에는 null을 넣으면 된다.

### Method
- `elements()` : value들만 묶어서 반환해준다.
- `keys()` : key들만 묶어서 반환해준다.
- `keySet()` : Set 자료형으로 key들을 묶어서 반환해준다.
    - 반환 값을 Set으로 받아서 `itertator()`를 통해 값을 하나씩 사용 가능
