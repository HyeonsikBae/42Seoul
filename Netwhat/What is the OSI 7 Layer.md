## What is the  OSI 7 Layer

### OSI 7 Layer

- 네트워크 통신 과정을 7개의 계층으로 구분한 산업 표준 참조 모델
- 각 계층은 하위 계층의 기능만을 이용하고, 상위 계층에게 기능을 제공한다.
- 아래 표와 같이 구성되어 있다.

| Floor | Layer        | PDU      | Example Protocols                   |
| ----- | ------------ | -------- | ----------------------------------- |
| 7     | Application  | Data     | HTTP, FTP, POP, SMTP, DNS, SSH      |
| 6     | Presentation | Data     | IMAP, FTP, MPEG, JPEG, SSL, SSH     |
| 5     | Session      | Data     | API'S, SOCKETS                      |
| 4     | Transport    | Segments | TCP, UDP, ARP, RTP, ECN, SCTP, DCCP |
| 3     | Network      | Packets  | IP, IPSec, ICMP, IGMP               |
| 2     | Data Link    | Frames   | Ethernet, MAC, LLC, PPP             |
| 1     | Physical     | Bits     | Ethernet, Bluetooth, USB            |

- PDU : Process Data Unit
  - 각 계층에서 전송되는 데이터의 단위

### Physical Layer

- Encoding : 0과 1의 데이터를 전기적 신호인 아날로그 신호로 바꾸어 다른 시스템에 전송
- Decoding : 아날로그 신호를 받아 0과 1의 데이터로 해석
- 물리적 매체로 연결된 두 시스템이 Encoding과 Decoding을 통해 데이터를 주고받을 수 있게 하는 모듈
- 물리계층은 PHY 내부에 물리적으로 구현되어 있다.
- 허브, 리피터, 라우터, 케이블 등 하드웨어와 관련이 있는 계층이다.

### Data Link Layer

- 
- 버스에서 원하는 목적지에만 데이터를 보낼 수 있다? > 스위치가 해 줌
- 라우터가 다른 네트워크끼리도 통신할 수 있게 해 줌.
- 송신자가 수신자에게 데이터를 보낼 때, 데이터 앞 뒤에 특정 비트열을 붙인다~
- 같은 네트워크 내에서 여러 시스템들이 데이터를 주고받기 위해 필요한 모듈
- Framing 은 Data-link Layer에 속하는 작업들 중 하나이다.
- Framing : 원본 데이터의 시작과 끝을 감싼 것.
- 랜카드 내부에 물리적으로 구현되어 있다.

### Network Layer

- 패킷 : 주소 + 데이터라고 하자.

- 라우터가 패킷 받고 까봐서 네트워크 내에 해당 주소가 없으면 다시 패킷 포장 후 상위 라우터로 전달 전달 전달

- 해서 적절한 라우터로 보내.. 이건 라우팅 공부해야 함

  그렇게 보내다보내다 해당 IP 갖고있는 라우터가 해당 IP로 패킷을 보냄.

- routing : IP 주소를 이용해 길 찾는 거

- forwarding : 자신 다음 라우터에 데이터 넘겨주는 것

- 많은 네트워크가 연결된 inter-network 속에서 목적지 컴퓨터에 데이터 넘겨주기 위해 routing, forwarding 하는거가 network layer다

- 운영체제의 커널에 SW적으로 구현되어있다~~~~

### Transport Layer

- 포트번호 : 하나의 컴퓨터에서 동시에 실행되고 있는 프로세스들이 서로 겹치지 않게 가져야하는 정수 값
- 송신자가 데이터에 수신할 포트번호 알고 있어야 해~~
- 포트번호를 사용해서 도착지 컴퓨터의 최종 도착지인 프로세스까지 데이터가 도달하게 하는 모듈
- 운영체제의 커널에 SW적으로 구현되어있다

### Application Layer

- TCP/IP가 요즘 쓰여~~~~ 5, 6, 7 Layer가 7 Layer로 묶여버렸으
- HTTP 로 인코딩 디코딩 된다.



MVC 패턴은 SW 아키텍처중 하나인데, 

SW아키텍처 중엔 Layered Architecture 라는게 있다.

Layerd 아키텍처 따르는 대표적인 예가 네트워크 시스템이다.

네트워크 시스템은 하나의 커다란 SW라고 할 수 있다.

OSI 7 layer 모델은 거대한 넷웤 SW의 구조를 설명하는 것이다.