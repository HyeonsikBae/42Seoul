## memset

- val을 size만큼 dest에 대입하는 함수

- SYNOPSIS

  ```c
  void	*memset(void *dest, int val, size_t size)
  ```

- CODE

  ```c
  size_t	count;
  
  count = 0;
  while (count < size)
      *((char*)dest + count++) = (unsigned char)val;
  return (dest);
  ```
  
- 동작
  1. count가 size보다 작으면 반복

     1-1) dest의 count번째 인덱스에 val 값 대입

  2. dest 반환