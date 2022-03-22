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

## OSI 1계층 Physical Layer
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
  

Solarized dark             |  Solarized Ocean
:-------------------------:|:-------------------------:
![ML_decision_tree_3_0](https://user-images.githubusercontent.com/53929665/99183236-a9e9d000-277d-11eb-80ff-9351fd56f5b6.png)  |  ![ML_decision_tree_3_0](https://user-images.githubusercontent.com/83754224/159127650-4655dcf7-6a33-4196-a501-615e127f385a.png)