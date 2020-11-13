## What is the  Class

### Class

- IP 주소에서 네트워크 영역과 호스트 영역을 나누는 방법.
  - 네트워크 주소 : IP 기기가 속해있는 네트워크 구분에 사용
  - 호스트 주소 : 네트워크 안에 있는 IP기기 구분에 사용

```
Class A : Network .   Host  .   Host  .   Host 
Class B : Network . Network .   Host  .   Host
Class C : Network . Network . Network .   Host
```

- A Class

  - 하나의 네트워크가 가질 수 있는 호스트 수가 제일 많은 클래스

  - IPv4에서 맨 앞자리가 0인 경우. 
    - __0XXX XXXX__ . XXXX XXXX . XXXX XXXX . XXXX XXXX
    - 약속에 의해 첫 옥텟 1 ~ 126 까지 사용.
    - 호스트 주소의 개수 : 2^24 - 2 (모든 값이  0은 네트워크 주소, 1은 브로드캐스트 주소)

- B Class

  - IPv4에서  맨 앞자리가 10인 경우.
    - __10XX XXXX . XXXX XXXX__ . XXXX XXXX . XXXX XXXX
    - 약속에 의해 첫 옥텟 128 ~ 191 까지 사용.
    - 호스트 주소의 개수 : 2^16 - 2

- C Class

  - IPv4에서 맨 앞자리가 110인 경우.
    - __110X XXXX . XXXX XXXX . XXXX XXXX__ . XXXX XXXX
    - 약속에 의해 첫 옥텟 192 ~ 223 까지 사용.
    - 호스트 주소의 개수 : 2^8 - 2

- D Class

  - Multicast 를 위해 존재하는 네트워크

  - IPv4에서 맨 앞자리가 1110인 경우.
    - __1110 XXXX . XXXX XXXX . XXXX XXXX__ . XXXX XXXX
    - 약속에 의해 첫 옥텟 224 ~ 239 까지 사용.
    - 호스트 주소의 개수 : 2^8 - 2

- E Class

  - 미래에 사용될 용도로 구분해 놓은 네트워크

  - IPv4 에서 맨 앞자리가 1111인 경우.
    - __1111 XXXX . XXXX XXXX . XXXX XXXX__ . XXXX XXXX
    - 약속에 의해 첫 옥텟 240 ~ 255 까지 사용.
    - 호스트 주소의 개수 : 2^8 - 2
