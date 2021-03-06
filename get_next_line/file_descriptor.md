## file descriptor

리눅스 혹은 유닉스 계열의 시스템에서 프로세스가 파일을 다룰 때 사용하는 개념.

프로세스에서 특정 파일에 접근할 때 사용하는 추상적인 값으로, Non-negative Integer 값을 갖는다.

- file descriptor 값
  - 프로그램이 실행될 때, file descriptor는 표준입력, 표준출력, 표준에러에 0, 1, 2라는 정수를 할당한다.
  - 이후에 열리는 파일들에 대해선 작은 값부터 순차적으로 fd 값을 할당한다.
  - OPEN_MAX는 하나의 프로세스가 열 수 있는 파일의 수로 정의된 상수이다.
- file descriptor 동작 특징
  - 처음 open하는 파일이 있으면 할당되지 않은 fd 값 중, 제일 작은 값이 파일에 fd 값으로 할당된다.
  - fd를 사용해 파일을 다시 불러오면 읽던 곳을 기억하고 불러낸다.