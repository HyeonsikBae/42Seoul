## memcpy

- src를 num만큼 dest에 복사하는 함수

- SYNOPSIS

  ```c
  void	*memcpy(void *dest, const void *src, size_t num)
  ```

- CODE

  ```c
  int count;
  
  count = 0;
  if (dest == src)
      return (dest);
  while (count < num)
  {
      *((unsigned char*)dest + count) = *((unsigned const char*)src + count);
      count++;
  }
  return (dest);
  ```
  
- 동작
  1. dest와 src가 같으면 dest 반환.

  2. num만큼 dest에 src를 복사하고 dest 반환.