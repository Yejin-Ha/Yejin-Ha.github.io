---
layout: post
title:  "[LINUX]VI의 기본 명령어"
subtitle: VI의 기본 명령어
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
# VI(visual editor)
- LINUX / UNIX 시스템에서 사용하는 텍스트 편집기
- 3가지 모드(명령, 입력, 실행)로 구분하여 사용할 수 있다.
    ![VI_mode](/assets/img/Linux/VI_mode.png)
- VIM - VI의 업그레이드 버전으로 VI와 같은 역할을 하지만 특정 위치에 있는 단어 or 의미있는 특별한 단어를 다른 색으로 표시해줘서 비교적 알아보기 쉽다.
<br>
<br>

## <span style="color:#da7c7c">1. 입력 모드</span>
- 글자를 입력할 수 있는 상태로 `a`, `i`, `o`를 눌러서 접근한다.
![vi_insert_mode](/assets/img/Linux/VI_insert.JPG)
<br>

## <span style="color:#da7c7c">2. 명령 모드</span>
- `esc`를 눌러서 실행한다.
<table>
<tr>
    <th>방향키 대신 사용하는 명령어</th>
    <td>h - 왼쪽 방향키<br/>
    j - 아래 방향키<br/>
    k - 위 방향키<br/>
    l - 오른쪽 방향키</td>
</tr>
<tr>
    <th>0(zero)</th>
    <td>행의 처음으로 이동</td>
</tr>
<tr>
    <th>$</th>
    <td>행의 마지막으로 이동</td>
</tr>
<tr>
    <th>gg / G</th>
    <td>문서의 처음 / 마지막으로 이동</td>
</tr>
<tr>
    <th>x / X</th>
    <td>현재 커서의 뒷 / 앞 글자 삭제</td>
</tr>
<tr>
    <th>u</th>
    <td>undo(실행 전으로)</td>
</tr>
<tr>
    <th>ctrl + r</th>
    <td>redo(실행 앞으로)</td>
</tr>
</table>
<br/>

## <span style="color:#da7c7c">3. EX(실행) 모드</span>

- `:`, `/`, `?`를 통해 모드에 접근한다.
- `/`, `?` - 색인(검색) 모드가 된다.
    - `/`와 `?`는 같은 역할을 하지만 결과를 찾는 방향이 반대다.
    - `/[찾을내용]` - 파일 안에서 원하는 내용을 위에서부터 찾는다.
    - `n` - 파일 안에 결과에 해당하는 내용이 많으면 `n`을 통해 다음 결과를 확인할 수 있다.
    - `N` - `n`과 같은 역할을 하지만 방향이 반대(이전의 결과를 확인할 수 있다.)

- `:` - 저장하는 명령어
<table>
<tr>
    <th>:w [file_name]</th>
    <td>현재 편집하고 있는 텍스트를 file_name으로 저장한다.</td>
</tr>
<tr>
    <th>:wq</th>
    <td>저장하고 나가기</td>
</tr>
<tr>
    <th>:q</th>
    <td>나가기(저장하지 않으면 경고가 나옴)</td>
</tr>
<tr>
    <th>:q!</th>
    <td>저장하지 않고 나가기</td>
</tr>
<tr>
    <th>:![명령어]</th>
    <td>VI 환경에서 shell의 명령을 실행한다.<br/>
    - VI와 shell을 왔다갔다 하기 번거로울 경우 주로 사용한다.</td>
</tr>
<tr>
    <th>:.![명령어]</th>
    <td>shell에서 수행된 명령의 결과를 문서에 포함한다.</td>
</tr>
<tr>
    <th>:(시작위치),(끝위치)s/(찾을패턴)/(변경할패턴)/(g)</th>
    <td>시작 위치~끝 위치 사이에서 원하는 패턴을 찾고 변경한다.<br/>
    g 옵션을 주면 해당하는 모든 라인의 부분을 변경하고 옵션을 주지 않으면 처음 찾은 부분만 변경</td>
</tr>
<tr>
    <th>:e [file_dir]</th>
    <td>해당하는 파일을 VI편집기로 열기</td>
</tr>
</table>
