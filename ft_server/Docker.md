# Docker

---

## Docker 란?

컨테이너라고 하는 가벼운 단위에서 어플리케이션을 실행하기 위한 플랫폼이다.

기존의 느린 서비스 배포 프로세스를 단축시키기 위해 가상 머신이 등장했지만, 실제로 사용되는 기술은 Docker 컨테이너이다.

컨테이너를 사용하여 어플리케이션을 보다 쉽게 생성, 배포 및 실행할 수 있도록 설계된 도구로써 DevOps(개발 + 운영)도구 체인의 일부이다.

SW 실행에 필요한 라이브러리 및 기타 종속성 등을 하나의 패키지로 만든다.

- Docker 활용 사례

  1. 구성 단순화

     하나의 Configuration으로 모든 플랫폼에서 실행 가능.

  2. 코드 관리

     일관된 환경 제공으로 개발을 편하게 만들어준다.

  3. 개발 생산성 향상

     개발 환경을 운영 환경에 최대한 가깝게 복제 가능

  4. 어플리케이션 격리

     Web Server와 연결된 API 서버 격리가 필요할 경우에, 다른 컨테이너에서 API 서버 실행 가능

  5. 빠른 배포

     컨테이너가 OS 부팅하지 않고 어플리케이션 실행하므로 Docker 컨테이너를 빠르게 만들 수 있다.

### Docker Architecture

- Docker Engine

  Docker 시스템의 핵심. Client-Server Architecture를 따르며 Host 시스템에 설치된다.

  구성 요소

  - Server : docker daemon. Docker Image 생성 및 관리
  - REST API : Docker daemon에게 지시하는 용도
  - CLI : Docker 명령 입력에 사용되는 Client.

- Docker Client

  User와 Docker가 상호 작용하도록 도와주는 역할. docker 명령을 docker daemon으로 전달한다.

  Docker Client는 둘 이상의 docker daemon과 통신이 가능하다.

- Docker Registry

  Docker Image가 저장된 위치. docker pull, docker run을 통해 docker image를 Docker Registry에서 가져오며 docker push를 통해 docker image가 Registry에 저장된다.

- Docker Object

  Docker로 작업할 때 사용되는 이미지, 컨테이너, 볼륨, 네트워크를 Docker Object라고 표현한다.

- Image

  Docker Container를 만드는 설명이 포함된 읽기 전용 템플릿.

- Container

  Docker Image를 실행하면 생성되는 Docker Container.

  모든 어플리케이션 및 환경은 해당 Container에서 실행된다.

- Volume

  Docker가 생성하고, Docker Container에서 사용하는 영속적인 데이터가 저장되는 위치.

  쓰기 가능한 데이터를 유지해야 한다면 볼륨을 사용하는 것이 좋다.

- Network

  모든 격리된 Container가 통신하는 통로

  5개늬 네트워크 드라이버가 있다.

  1. Bridge : 기본 네트워크 드라이버. 어플리케이션이 독립형 컨테이너에서 실행될 때 사용
  2. Host : 컨테이너와 호스트간 네트워크 격리 제거. 컨테이너와 호스트 간 네트워크 격리가 필요하지 않을 경우 사용
  3. Overlay : 컨테이너가 다른 Docker 호스트에서 실행 중이거나 Swarm 서비스가 여러 어플리케이션에 의해 형성될 경우 사용
  4. None : 모든 네트워킹 비활성화
  5. macvlan : 물리적 주소처럼 보이도록 mac 주소를 컨테이너에 할당. VM 설정을 마이그레이션 하는 동안 컨테이너가 물리적 장치처럼 보이게 하려는 경우에 사용.
