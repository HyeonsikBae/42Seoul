## What is the  TCP and UDP

### TCP (Transmission Control Protocol)

- 신뢰성있는 데이터 통신을 가능하게 해 주는 프로토콜

- TCP는 데이터에 TCP Header를 추가한 Segment단위의 데이터를 전송한다.

- TCP의 특징

  - 3-way handsahking을 통한 연결, 4-way handshaking을 통한 연결 해제 - 양방향 통신
  - Flor Control (흐름 제어)
  - Congestion Control (혼잡 제어)
  - Error Detection (오류 감지)
  - 높은 신뢰성 보장
  - UDP에 비해 느린 속도
  - Full-Duplex, Point to Point

- TCP Header Field

  | Field                          | Description                                                  |
  | ------------------------------ | ------------------------------------------------------------ |
  | Source Port / Destination Port | 프로세스에 할당된 Port 번호                                  |
  | Sequence Number                | 세그먼트 전송 시, 각 바이트마다 매겨진 순서                  |
  | Acknowledgement Number         | 수신 프로세스가 제대로 수신한 바이트 수를 응답하기 위한 번호 |
  | Data Offset                    | TCP Segment가 시작되는 위치를 기준으로 데이터 시작 위치      |
  | Reserved                       | 예약 필드                                                    |
  | Window                         | 수신 윈도우의 버퍼 크기를 지정하기 위한 수                   |
  | Checksum                       | 오류 검출을 위한 필드                                        |
  | Urgent Pointer                 | 긴급 데이터 처리를 위한 것                                   |

- TCP Header Flag bit

  | Flag Bit | Description                                                  |
  | -------- | ------------------------------------------------------------ |
  | URG      | Urgent Pointer Field가 유효한지를 나타내는 플래그            |
  | ACK      | Acknowledgement Number Field가 유효한지를 나타내는 플래그    |
  | PSH      | 현재 세그먼트에 포함된 데이터를 상위계층에 즉시 전달하도록 지시하는 플래그 |
  | RST      | 연결이 유효하지 않은 세그먼트에 대한 응답용 플래그           |
  | SYN      | 연결 설정 요구를 의미하는 플래그                             |
  | FIN      | 연결 종료 의사 표시를 나타내는 플래그                        |

  

### UDP ( User Datagram Protocol)

- 데이터를 데이터그램 단위로 처리하는 프로토콜

- UDP는 데이터에 UDP Header를 추가한 Segment단위의 데이터를 전송한다.

- 데이터 전송의 신뢰성보단 속도가 중요할 때 사용한다.

- UDP의 특징

  - Connectionless
  - Error Detection
  - TCP에 비해 빠른 속도
  - 

- Error Detection 있지

- 데이터 신뢰성 안중요할 때 써 .. 영상 스트리밍처럼~

- TCP는 4계층에서 데이터 쪼개지만, UDP에선 직접 Application  단에서 쪼개야 함.

- 1:1, 1:N, N:M 통신

- UDP Header

  | Field                          | Description                                          |
  | ------------------------------ | ---------------------------------------------------- |
  | Source Port / Destination Port | 프로세스에 할당된 Port 번호                          |
  | Length                         | 헤더와 데이터를 포함한 전체 길이. 바이트 단위로 표시 |
  | Checksum                       | 오류 검출을 위한 필드                                |



### TCP / UDP 차이점

|                | TCP           | UDP                |
| -------------- | ------------- | ------------------ |
| 연결 방식      | 연결형 서비스 | 비연결형 서비스    |
| 패킷 교환 방식 | Byte Stream   | Datagram           |
| 전송 순서      | 순서 보장     | 순서 보장하지 않음 |
| 수신 여부 확인 | 확인          | 확인하지 않음      |
| 통신 방식      | 1:1           | 1:1. 1:N, N:M      |
| 신뢰성         | 높다          | 넞더               |
| 속도           | 느리다        | 빠르다             |
| 에러 복구      | 복구 실행     | 복구하지 않음      |

