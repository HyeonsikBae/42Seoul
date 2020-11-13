## strlen

- 매개변수로 들어오는 문자열의 길이를 반환해주는 함수

- SYNOPSIS

  ```c
  size_t	strlen(const char *string)
  ```

- CODE

  ```c
  size_t	length;
  
  length = 0;
  while (*(string + length))
      length++;
  return (length);
  ```
  
- 동작
  1. 사이즈를 체크할 변수 length 선언 및 초기화

  2. string의 length번째 주소에 값이 있으면 반복

     2-1) length값 증가

  3. string의 length번째 주소에 값이 없으면 __length 값__ 반환.