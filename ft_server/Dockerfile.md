# Dockerfile

---

Docker는 Dockerfile의 구성 요소를 실행하며 이미지를 빌드한다.

Dockerfile엔 유저가 커맨드 라인에 입력한 명령어들이 모여 있다.

- FROM

  빌드 할 이미지의 기반을 나타낸다.

  과제에선 FROM debian:buster 라는 커맨드를 통해 OS를 나타냈다.

- COPY

  파일을 이미지에 추가한다.

  COPY <복사하고자 하는 파일> <이미지 내 파일이 복사될 경로> 로 사용한다.

- RUN

  커맨드를 실행한다.

- ENTRYPOINT

  컨텡너가 시작될 때, 실행되는 명령어이다.