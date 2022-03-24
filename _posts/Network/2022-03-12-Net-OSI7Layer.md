---
layout: post
title:  "[Network]OSI 7 Layer란?"
subtitle: OSI 7 계층
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
# OSI 7 Layer
프로토콜을 기능 별로 나눈 것으로 각 계층은 하위 계층의 기능을 이용하고, 상위 계층에게 기능을 제공한다.

<br/>

## <span style="color:#da7c7c">OSI 1계층 Physical Layer</span>
- 전기적, 물리적 신호를 전달한다.
- **cable, connector, bit**
- **클럭(clock) 신호** : 0, 1로 이루어진 전기적/물리적 신호를 보낼 때 클럭 신호를 함께 보내서 데이터를 보낸다고 인식 시킨다.
- **`Ethernet Connector`**
    - 1, 2, 3, 6번 선은 통신을 위한 선이고 다른 선들은 전기가 통하지 않는다.
    - 네트워크 관리사 시험 출제 내용
        > 녹주청갈 ⇒ T568A <br/>
        주녹청갈 ⇒ T568B <br/>
        색이 칠해지는 과정은 빗금, 줄, 빗금, 줄 순서가 반복된다.
    
    <aside><span style="background-color:#fffdd6">💡 <SPAN STYLE="font-weight:bold">PoE(Ethernet 전원 장치) 기능</span> : 4, 5, 7, 8번 선에 전기를 보내서 케이블을 통해 전력을 받을 수 있게 한다.</span></aside>

    ![Ethernet_connector1](/assets/img/Network/ethernetConnector1.png)  |  ![Ethernet_connector2](/assets/img/Network/ethernetConnector2.png)
    |:-------------------------:|:-------------------------:|

- Straight-Through cable VS Crossover cable  
    | Straight-Through cable | Crossover cable |
    | --- | --- |
    | - 신호가 같은 번호의 선으로 들어감(1 -> 1, 2 -> 2)<br/>- 이런 형태면 연결이 되지 않는 장비도 존재한다. | - 1, 2번 라인은 반대편 3, 6번 라인으로 3, 6번 라인은 반대편 1, 2번 라인으로 들어간다. <br/> - 보통의 가정집은 이런 형태임 |
    | ![Straight-throughCable](/assets/img/Network/straight-throughCable.png)  |  ![CrossoverCable](/assets/img/Network/crossoverCable.png) |


- 광케이블 Fiber cable
    - 무리하게 구부릴 경우 섬유(유리)가 끊어져서 신호 전달이 끊긴다.

    | Single mode | Multi mode |
    | --- | --- |
    | - 단일 경로 <br/>- 하나의 신호만 보낼 수 있음<br/> - 속도가 빠름 <br/>- 가격이 비쌈 | - 여러 신호를 다중으로 보낼 때 사용 <br/>- 신호(빛)을 입사각, 반사각으로 계속 바꿔가면서 전달한다. <br/>- 가격이 비쌈 |

<br/>
<br/>

## <span style="color:#da7c7c">OSI 2계층 Data Link Layer</span>
- 물리 게층과 네트워크 계층의 연결을 돕는 계층
- `MAC 주소`(물리적 주소)
- 데이터 링크 계층의 정보는 계속 변한다.
- 네트워크 전달 방식
    1. Circuit : 길을 정하고 연결하는 것
    2. Packet : 데이터를 잘라서 전송(header + payload) -> 보통의 인터넷 방식
- **Frame Type**
    - Frame : data가 보내지는 형식(1 ~ 7계층이 존재)
    ![Ethernet_Frame](/assets/img/Network/EthernetFrame.png)
        - Preamble : 전기가 불규칙하게 흐르고 있기 때문에 Frame의 시작을 알리기 위해 8byte 동안 같은 신호를 보낸다. 마지막은 11로 끝나서 이 뒤(Destination Address)부터 의미있는 데이터가 있다고 인지시킨다. -> **물리 계층**
        - Destination Address : MAC 주소, 물리적 주소 -> **네트워크 계층**
        - Source Address : MAC 주소, 물리적 주소 -> **네트워크 계층**
        - Type
        - Data : 실제 보내는 데이터가 최대 1500byte라서 보내려는 데이터가 이를 초과한다면 사이즈에 맞게 살라서 여러 Frame으로 전송한다.
- **MAC 주소**
    - **EUI-48**(00-0E-35-80-6F), **EUI-64**(00-0E-35-FF-FE-05-80-6F) 방법이 있다.
    - **EUI-48**로는 모든 장비의 MAC 주소를 할당하기에 무리가 있어서 **EUI-64**로 보완

<br/>
<br/>

## <span style="color:#da7c7c">OSI 3계층 Network Layer</span>
- IP(Internet Protocol) Address : 집 주소와 같은 역할을 한다. 규칙이 있음
    <table>
    <tr>
        <th>IPv4</th>
        <td>redo(실행 앞으로)</td>
    </tr>
    <tr>
        <th>IPv6</th>
        <td>redo(실행 앞으로)</td>
    </tr>
    <tr>
        <th>NAT</th>
        <td>redo(실행 앞으로)</td>
    </tr>
    <tr>
        <th>NAT-PAT</th>
        <td>redo(실행 앞으로)</td>
    </tr>
    </table>