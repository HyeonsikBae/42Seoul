## putstr_fd

- 매개변수로 들어오는 파일 디스크립터에 매개변수로 들어오는 문자열을 출력하는 함수

- SYNOPSIS

  ```c
  void	putstr_fd(char *string, int fd)
  ```

- CODE

  ```c
  if (!string)
      return ;
  write(fd, string, strlen(string));
  ```
  
- 동작
  1. string이 비어있으면 Early return

  2. string이 비어있지 않으면 fd에 string의 길이만큼 string을 출력한다.