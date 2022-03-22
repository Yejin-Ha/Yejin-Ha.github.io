---
layout: post
title:  "[LINUX]정규표현식 Regular Expression"
subtitle: 정규표현식
categories: tech
tags: linux
comments: true
---
**Contents**
- [VI](#vivisual-editor)
    1. [입력모드](#1-입력-모드)
    2. [명령모드](#2-명령-모드)
    3. [실행모드](#3-ex실행-모드)

---
# 정규표현식
- 어떤 문자열의 집합을 묘사하는데 사용되는 text 문자열
- 정해진 구문 규칙에 따른다.

<table>
<tr>
    <th>^</th>
    <td>줄의 시작을 나타내지만 문맥에 따라서는 문자 집잡의 의미를 반대로 해석</td>
</tr>
<tr>
    <th>*</th>
    <td>바로 앞의 문자열이나 정규 표현식에서 0개 이상 문자가 반복된다.</td>
</tr>
<tr>
    <th>.</th>
    <td>오직 한 개의 글자</td>
</tr>
<tr>
    <th>[..]]</th>
    <td>문자들의 집합</td>
</tr>
<tr>
    <th>\</th>
    <td>특수 문자를 원래 문자 의미 그대로 해석하게 해줌(escape)</td>
</tr>
<tr>
    <th>\< , \></th>
    <td>단어의 시작, 끝</td>
</tr>
<tr>
    <th>A\{n\}</th>
    <td>문자 A를 n번 반복</td>
</tr>
<tr>
    <th>A\{n,\}</th>
    <td>문자 A를 적어도 n번 반복</td>
</tr>
<tr>
    <th>A\{n,m\}</th>
    <td>문자 A를 n~m번 반복</td>
</tr>
</table>