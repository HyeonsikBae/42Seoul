## putendl_fd

- 매개변수로 들어오는 파일 디스크립터에 매개변수로 들어오는 문자열과 개행을 출력하는 함수

- SYNOPSIS

  ```c
  void	putendl_fd(char *s, int fd)
  ```

- CODE

  ```c
  {
  	char    c = '\n';
  
  	if (!s)
  		return ;
  	write(fd, s, ft_strlen(s));
  	write(fd, &c, 1);
  }
  ```
  
- 동작
  
  1. s 값이 비어있으면 함수 종료
  2. s 출력
  3. 개행 출력