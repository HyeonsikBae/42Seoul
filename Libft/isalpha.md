## isalpha

- 문자가 알파벳인지 판별하는 함수

- SYNOPSIS

  ```c
  int	isalpha(int c)
  ```

- CODE

  ```c
  {
  	if (c >= 'A' && c <= 'Z')
  		return (1);
  	else if (c >= 'a' && c <= 'z')
  		return (2);
  	else
  		return (0);
  }
  ```
  
- 동작
  1. c 가 대문자이면 1 반환
2. c 가 소문자이면 2 반환
  3. c 가 문자가 아니면 0 반환
