## putchar_fd

- 매개변수로 들어오는 파일 디스크립터에 매개변수로 들어오는 문자를 출력하는 함수

- SYNOPSIS

  ```c
  void	putchar_fd(char c, int fd)
  ```

- CODE

  ```c
  {
  	if (sizeof(c) == 1)
  		write(fd, &c, 1);
  	else
  		write(fd, &c, 2);
  }
  ```
  
- 동작
  1. 문자 c의 크기가 1이면 1byte 크기의 c 출력
2. 문자 c의 크기가 1이 아니면 2byte 크기의 c 출력