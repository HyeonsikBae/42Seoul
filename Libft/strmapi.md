## strmapi

- 문자열 s에 함수 f를 적용시킨 뒤 반환하는 함수

- SYNOPSIS

  ```c
  char	*strmapi(char const *s, char (*f)(unsigned int, char))
  ```

- CODE

  ```c
  long	len = 0;
  char	*result;
  if (!s)
      return (NULL);
  if (!(result = malloc(sizeof(char) * (strlen(s) + 1))))
      return (NULL);
  while (*(s + len))
  {
      *(result + len) = f(len, *(s + len));
      len++;
  }
  *(result + len) = '\0';
  return (result);
  ```
  
- 동작
  1. 입력으로 들어오는 문자열 s의 주소가 비어있는 경우 Early return.

  2. 반환할 char형 포인터 변수 result에 메모리 할당에 실패할 경우 Early return.

  3. 문자열 s의 len 번째 포인터 값이 있을 경우 반복
  
     3 - 1) result의 len번째 주소에 s의 len 번째 값에 함수 f를 적용하여 대입
  
  4. result의 마지막 주소에 널값 대입
  
  5. result 반환
  