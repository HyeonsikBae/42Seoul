## isascii

- 문자가 ascii 코드 내 값인지 판별하는 함수

- SYNOPSIS

  ```c
  int	isascii(int c)
  ```

- CODE

  ```c
  {
  	if (c >= 0 && c <= 127)
  		return (1);
  	else
  		return (0);
  }
  ```
  
- 동작
  
  1. c 가 ascii 코드 내 값이면 1 반환
  2. c 가 ascii 코드 내 값이 아니면 0 반환