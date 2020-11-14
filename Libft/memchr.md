## memchr

- ptr에서 num 크기 내에 value가 있는지 찾아 해당 포인터 주소를 반환하는 함수

- SYNOPSIS

  ```c
  void	*memchr(void *ptr, int value, size_t num)
  ```

- CODE

  ```c
  size_t	count = 0;
  while (count < num)
  {
      if (*(unsigned char*)ptr + count) == (unsigned char)value)
          return (ptr + count);
      count++;
  }
  return (NULL);
  ```
  
- 동작
  1. count에 0 대입

  2. count가 num보다 작으면 반복

     2-1) ptr + count 번째 값이 value와 같으면 ptr+count 반환
  
     2-2) count 증가
  
  3. 반복문 내에서 value값 찾지 못하면 NULL 반환
  