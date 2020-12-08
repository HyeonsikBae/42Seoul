## isalnum

- 문자가 알파벳인지 판별하는 함수

- SYNOPSIS

  ```c
  int	isalnum(int c)
  ```

- CODE

  ```c
  {
  	if ((c >= 'a' && c <= 'z')
          || (c >= 'A' && c <= 'Z')
          || (c >= '0' && c <= '9'))
  		return (1);
  	else
  		return (0);
  }
  ```
  
- 동작
  
  1. c 가 문자 또는 숫자이면 1 반환
  2. c 가 문자나 숫자가 아니면 0 반환