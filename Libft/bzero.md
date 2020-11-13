## bzero

- 포인터 s에 n만큼 값을 0으로 채우는 함수

- SYNOPSIS

  ```c
  void	bzero(void *s, size_t n)
  ```

- CODE

  ```c
  size_t count = 0;
  while (count < n)
      *((char*)s + count++) = 0;
  ```
  
- 동작
  1. count가 n 보다 작을 경우 반복

     1-1) 문자열 s의 count 번째 주소의 값에 0 대입
