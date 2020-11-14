## What is the  OSI 7 Layer

SW Architecture 중엔 Layered Architecture라는 것이 있다.

Layered Architecture 를 따르는 대표적인 예가 Network System이고, 이 Network System은 하나의 커다란 Software라고 할 수 있다.

OSI 7 Layer 모델은 거대한 Network Software의 구조를 설명하는 것이다.

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

- 물리적으로 연결된 두 시스템 사이 데이터를 주고받기 위한 모듈
- Encoding : 0과 1의 데이터를 전기적 신호인 아날로그 신호로 바꾸어 다른 시스템에 전송
- Decoding : 아날로그 신호를 받아 0과 1의 데이터로 해석
- 물리계층은 PHY 내부에 물리적으로 구현되어 있다.
- 허브, 리피터, 라우터, 케이블 등 하드웨어와 관련이 있는 계층이다.

### Data Link Layer

- 물리적인 네트워크 사이에서 Data 전송을 담당하는 계층
- 물리계층으로 데이터 전송 시에 데이터 전송 오류를 감지하고 이럴 경우 재전송한다.
- 같은 네트워크 내에서 여러 시스템들이 데이터를 주고받기 위해 필요한 모듈
- Framing : 원본 데이터의 시작과 끝을 특정 비트열로 감싼 것.
- 랜카드 내부에 물리적으로 구현되어 있다.

### Network Layer

- 데이터를 목적지까지의 경로를 찾아 전송하는 계층
- 데이터에 주소 정보가 포함된 패킷을 전송
- inter-network 속에서 routing, forwarding을 통해 데이터를 전송한다.
- 운영체제의 커널 냅부에 소프트웨어로 구현되어있다

### Transport Layer

- End Point 간 신뢰성 있는 데이터를 전송하게 해주는 계층
- 데이터에 포트 정보가 포함된 세그먼트를 전송
- 오류검출 및 복구, 흐름제어, 중복검사 수행
- 운영체제의 커널에 SW적으로 구현되어있다
- TCP, UDP가 Transport Layer에 속한다.

### Session Layer

- 응용 프로세스가 통신을 관리하기 위한 방법을 정의해주는 계층
- 세션을 만들고, 유지하고, 종료하며 전송 중단 시에 복구해주는 기능이 있다.
- OS가 Sessiong Layer에 속한다.

### Presentation Layer

- 응용계층으로부터 전달받거나 전송하는 데이터의 인코딩, 디코딩이 이루어지는 계층
- 응용 계층에서 데이터를 이해할 수 있도록 응용프로그램에 맞춰 변환이 일어난다.
- 다음과 같은 세 가지의 기능을 가지고 있다.
  - 송신자로부터 받은 데이터를 해석하기 위한 응용계층 데이터 부호화
  - 수신자에서 데이터의 압축을 풀 수 방식의 데이터 압축
  - 데이터의 암호화, 복호화

### Application Layer

- End User 또는 Application이 Network에 접근할 수 있도록 해주는 계층
- 프로세스가 응용 계층에서 동작한다.

