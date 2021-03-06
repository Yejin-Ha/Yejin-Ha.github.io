---
layout: post
title:  "[Network]Network란?"
subtitle: Network란
categories: tech
tags: network
comments: true
---
#### Contents
- [Network란](#network란)
- [Protocol](#protocol-통신-규약)
    - [Network Device](#network-device)

<br>

---

# Network란
- 물리적으로 연결하여 대화할 수 있는 환경 또는 그러한 것

Network는 **연결 범위**에 따라 `LAN(Local Area Network)`, `WAN(Wide Area Network)`으로 구분할 수 있다.  
`LAN`의 사전적 정의는 **근거리 통신망**이지만 LAN의 범위는 일정하지 않아서 사람마다 기준이 다를 수 있다.

> 강의실에 있는 모든 PC는 하나의 스위치에 연결되어 있고 스위치는 공유기에 연결되어 있음 ⇒ LAN  
LAN끼리 연결되어 있음 ⇒ WAN
<br/>

그리고 **공용망**, **전용망(사설망)**, `VPN`으로도 구분할 수 있다.

- 공용망 - 외부에 공개되어 있는 IP 주소
- 전용망 - 주로 회사에서 사용하며 로컬 IP 주소라고도 한다.  
    - 외부에서 접근이 불가능하여 보안적 측면에서 안전하지만 추가적인 비용이 소모된다.
- `VPN` - 공용망에서 전용망으로 사용할 수 있는 통신망
<br/>

마지막으로 **data를 주고 받는 형태**에 따라 분류할 수 있다.
- Server & Client - Client가 Server에게 service(원하는 자료)를 요청하고, Server는 Client에게 service(자료)를 보내주는 형식
- `P2P`(Peer to Peer) - Server이자 Client가 되는 형식

    > Ex. 토렌트
    내(client)가 다운 받고(service) 다른 사람도 다운 받을 수 있게(server) 해주는 형식
<aside><span style="background-color:#fffdd6">💡 server : 제공하는 것 or 사람 &nbsp;/&nbsp; client : 이용하는 것 or 사람 &nbsp;/&nbsp; service : 요청된 것</span></aside>


<br>
<br>

# Protocol 통신 규약
- 네트워크로 서로 통신하기 위해 미리 정해 놓은 약속으로 종류가 매우 많다.
- 끝이 P로 끝나면 보통 Protocol의 약자라고 생각해도 된다
    > HTTP = Hyper Text Transfer Protocol
- `TCP/IP` 도 Protocol의 한 종류이다.

<aside><span style="background-color:#fffdd6">💡 TCP/IP - 현재 인터넷에서 컴퓨터들이 서로 정보를 주고받는데 쓰이는 통신 규약의 모음</span></aside>
<br>

## Network Device
<table>
 <tr>
     <th><i>Repeater</i></th>
     <td>• 거리가 멀면 전기 신호가 이동하면서 점점 약해지는데 중간에 Repeater를 지나가면 신호가 다시 세진다. <br/>
     → 2대의 장비만 연결 가능</td>
 </tr>
 <tr>
     <th><i>HUB</i></th>
     <td>• Repeater와 같은 역할이지만 장비를 여러 개 연결 가능(Multi port Repeater) <br/> 
     • 물리 계층[1, 전기신호]만 인지하며 데이터 링크 계층[2, 주소]은 인식하지 못함 <br/> 
     → 신호가 겹치면 충돌이 일어날 수 있음 <br/>  <br/> 
    • CSMA/CD <br/> 
    &nbsp;&nbsp;&nbsp;&nbsp; • HUB에서 사용하는 방식으로 충돌을 감지해서 데이터가 잘 전달될 수 있게 하는 용도 <br/> 
    &nbsp;&nbsp;&nbsp;&nbsp; • 데이터 링크 계층[2]에 존재함(신호를 전달하는 것은 물리 계층[1])</td>
 </tr>
 <tr>
    <th><i>Bridge</i></th>
    <td>• 데이터 링크 계층[2, 주소]을 인식하여 전송 받은 값을 적절한 곳으로 옮겨줌
 </td>
 </tr>
 <tr>
    <th><i>Switch</i></th>
    <td>• simplex : 송신만 or 수신만 가능 <br/> 
    • duplex : 송신, 수신 한번에 가능 <br/> 
    &nbsp;&nbsp;&nbsp;&nbsp; → Full(송신, 수신을 위해 독립된 회선을 사용하는 방식) / Half(한쪽이 수신하면 다른 쪽은 송신만 함) <br/>  <br/> 
    • Switch는 Full duplex 이며 신호가 겹쳐도 상관이 없어서 대부분 Switch를 사용하고 있다. <br/> 
    • MAC 주소를 기반으로 통신 <br/> 
    • HUB와 HUB를 연결</td>
 </tr>
  <tr>
    <th><i>Router</i></th>
    <td>• 네트워크 계층[3] 장비 <br/> 
    • 데이터가 이동할 때 Router를 지나면서 데이터 링크 계층[2]의 주소가 계속 변경되지만 네트워크 계층[3]의 정보를 이용하여 최적의 경로를 탐색한다. <br/> 
    • 일반적으로 LAN과 WAN을 연결함</td>
 </tr>
 </table>