---
layout: post
title:  "[JAVA]eclipse의 debug"
subtitle: for문과 while문에 대한 정리
categories: tech
tags: java
comments: true
---
**Contents**<br/>
eclipse에서 디버깅을 하는 과정과 방법에 대한 정리.

<br/>
<br/>

---
# 디버그 Debug
프로그래밍 중 발생하는 오류나 비정상적인 연산, 버그를 찾고 수정하는 것

<br/>

## <span style="color:#da7c7c">디버깅 방법</span>
### <span style="color:#da7c7c">1. breakpoint 생성</span>
아무런 설정을 하지 않고 디버깅을 하면 일반 실행과 다를게 없는 결과를 반환한다.  
- 디버깅을 할 부분을 **breakpoint**으로 지정해야한다.
- breakpoint를 여러 개 지정해서 원하는 코드 이전의 코드는 한 번에 실행할 수 있다.
- 원하는 코드를 마우스로 한 번 클릭한 후 `ctrl` + `shift` + `b`를 눌러서 다음 화면과 같이 왼쪽에 파란 점이 생기는 것을 확인할 수 있다.

    ![untitled](/assets/img/JAVA/debug/1.JPG)
    - 4번 라인과 6번 라인에 breakpoint를 지정하였다.

<br/>

### <span style="color:#da7c7c">2. 디버그 시작하기</span>
breakpoint를 지정했으면 `f11`을 눌러서 디버깅을 시작한다.

- 아래 이미지처럼 녹색 라인은 앞으로 실행할 코드를 표시하는 것이다.
    ![untitled](/assets/img/JAVA/debug/2.JPG)

- 오른쪽에 Variables를 통해 변수의 값이 변하는 과정을 확인할 수 있다.
    ![untitled](/assets/img/JAVA/debug/3.JPG)

- **resume(f8)**을 통해서 다음 브레이크 포인트까지의 코드를 한번에 실행할 수 있다.
- 계산이 진행된 후 이전 계산으로 돌아가는 방법은 없다.
    - 다시 시작해야한다...
- `step into(f5)` - 함수를 호출할 때 호출되는 과정을 모두 보여주는 실행
- `step over(f6)` - 함수를 호출하고 난 후의 과정을 보여주는 실행
- `ctrl` + `f2` - 디버깅 종료
