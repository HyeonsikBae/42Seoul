## What is the  DHCP

### DHCP (Dynamic Host Configuration Protocol)

- 해당 호스트의 IP주소와 TCP/IP 프로토콜의 기본 설정을 자동적으로 클라이언트에게 일정시간 제공해주는 인터넷 프로토콜이다.

- DHCP의 구성
  - DHCP Client
    - DHCP Server에 IP를 요청하고, IP를 부여받으면 TCP/IP 통신을 할 수 있다.
  - DHCP Server
    - Client로부터 IP 할당 요청이 오면, 설정된 범위 안에서 사용하고 있지 않은 IP를 Client에 부여한다.
  - DHCP Protocoal
    - BOOTP메시지 형식을 사용하며, IP 주소와 TCP/IP 기본 설정을 개별 클라이언트에 자동적으로 할당한다.

- DHCP의 장, 단점
  - DHCP의 장점
    - IP 관리의 편의성
      - DHCP 서버에서 IP를 자동할당하므로 IP충돌이 예방된다.
    - 네트워크 연결 설정 시간 단축
      - 특별한 설정 없이 PC를 네트워크와 연결 가능
  - DHCP의 단점
    - DHCP 서버의 다운
      - DHCP가 다운되면 IP할당이 불가능해져 인터넷 사용이 불가능해진다.
    - IP 자원의 고갈
      - 악의적인 공격으로 인해 서버의 IP자원이 고갈 될 우려가 있다.
    - UDP 기반 프로토콜
      - 네트워크 부하에 따라 IP할당이 지연되거나 실패할 수 있다.

- DHCP의 동작
  - DHCP 통신 흐름 (DORA)
    - Discover : Client가 DHCP서버를 찾기 위해 브로드캐스트로 전달하는 패킷
    - Offer : Server가 Discover 패킷을 받고나서 임대해줄 수 있는 네트워크 정보와 자신의 IP를 전달
    - Request : Client가 전달받은 네트워크 정보를 사용하겠다고 Server에 전달하는 패킷
    - Ack : Request를 받은 Server가 네트워크 정보를 임대
  - 임대
    - DORA를 통해 IP를 받는 과정.
    - iptime의 경우, 기본적으로 7200초로 설정되어 있음.
  - 갱신
    - 임대시간의 50% 지났을 때 갱신 시도. 성공하면 설정되어 있는 임대 시간만큼 추가 할당, 실패하면 갱신 보류
    - 임대시간의 87.5% 지났을 때 갱신 시도. 성공하면 설정되어 있는 임대 시간만큼 추가 할당, 실패하면 갱신 종료
  - 반환
    - DHCP에게 할당받았던 IP 반환.
    - 임대 시간 지나고도 통신이 되지 않을 경우, DHCP는 IP를 반환 받은 것으로 처리한다.