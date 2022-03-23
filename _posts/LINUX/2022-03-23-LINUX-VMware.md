---
layout: post
title:  "[LINUX]VMware란?"
subtitle: LINUX의 VMware 정리
categories: tech
tags: linux
comments: true
---
**Contents**
- 가상머신 VMware
    - [네트워크 방식](#네트워크-방식) - Host-only, NAT, Bridge
    - [Apache란?](#아파치-apache)

---
# 가상머신 VMware
CentOS로 Server, Client VM을 만들어 놨다는 가정 하에 정리하였다.
<br/>
<br/>

## <span style="color:#da7c7c">네트워크 방식</span>
1. **Host-only(Vmnet1)**
    - Host PC 만 통신이 가능하다 = **내부 통신만 가능**  
    - Server VN을 Host-only로 변경하면 Client VM과 통신이 불가능해진다.

3. **NAT(Vmnet8)**
    - **외부 통신이 가능**
    - HOST PC에서 IP를 할당받는다.(HOST PC는 공유기에서 IP 할당받음)

2. **Bridge(Vmnet0)**
    - **외부 통신이 가능**
    - 공유기에서 IP를 할당받는다.
    - HOST PC와 VM은 동일한 수준의 물리적 PC로 인식된다.
<br/>

<span style="background-color:#fffdd6">NAT와 Bridge의 차이는 **VMware가 IP 할당을 어디서 받느냐** 이다.</span>
<br/>
<br/>
<br/>


## <span style="color:#da7c7c">아파치 Apache</span>
리눅스에 Apache 서버를 설치하면 HTTP 서버를 동작시킬 수 있습니다. <br/>
HTTP는 80번 포트를 사용하는 웹 서버라고 생각하면 된다.<br/>
Server VM으로 웹 서버를 실행시킨 후 Client VM으로 접근하는 과정을 정리하였다. 
<br/>

### 설치 및 실행 방법
1. Server로 사용할 VM에 아파치를 설치한다.
    - `-y` : 설치하는 과정에서 발생하는 모든 질문에 응답을 yes로 설정
    ```shell
    [root@localhost ~]# yum -y install httpd
    ```

2. 웹 서버를 실행한다.
    - 아파치가 정상적으로 설치되었다면 다음 명령어를 통해 웹 서버를 실행한다.
    ```shell
    [root@localhost ~]# systemctl start httpd.service
    ```
    - 웹 서버 끄기
    ```shell
    [root@localhost ~]# systemctl stop httpd.service
    ```

3. 웹 서버가 정상적으로 실행되었는지 확인하기
    - `netstat` 를 통해 네트워크 연결상태, 라우팅테이블, 인터페이스 상태 등을 확인할 수 있다.
    ```shell
    [root@localhost ~]# netstat -atunp
    ```
    ![check_webserver](/assets/img/Linux/Apache_check1.JPG)
    - 웹 서버는 80번 포트이며 실행이된다면 80번이 나온다. Listening?
    - 자신의 IP 또는 127.0.0.1(localhost 와 같은 주소) 에 이미지와 같이 나오면 성공!
    
        |![check_ip](/assets/img/Linux/Apache_check2.JPG)|![check_ip](/assets/img/Linux/Apache_check3(1).JPG)|
        |:----:|:----:|
        |`ifconfig`로 확인한 ip|127.0.0.1|

    <br/>

    - 하지만 Server VM의 방화벽이 외부 접근을 막고있어서 Client VM으로 접속을 해보면 연결 실패가 뜬다. <br/>
        ![check_wrong_root](/assets/img/Linux/Apache_wrong.JPG)

4. 방화벽에 80번 포트 접근 추가하기
    - 다음 명령어를 통해 80번 포트의 접근 권한이 있는지 확인한다.
        ```shell
        [root@localhost ~]# iptables -nL
        ```
        ![check_iptables](/assets/img/Linux/Apache_iptables.JPG)
    - 80번 포트가 없는 것이 확인되었다. 다음 명령어를 통해 접근을 추가하자
        - `-i` : insert
        - `-p` : protocol
        ```shell
        [root@localhost ~]# iptables -I INPUT -p tcp --dport 80 -j ACCEPT
        ```
        ![asdf](/assets/img/Linux/Apache_iptables_accept.JPG)
        - 맨 위에 80번 포트가 추가된 것을 확인할 수 있다. 

<br/>
<br/>

이제 Client VM으로 접속이 가능하다.
![check_client](/assets/img/Linux/Apache_check4.JPG)

