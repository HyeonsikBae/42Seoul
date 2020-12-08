## strlcpy

- size만큼 src에서 dest로 복사하고, src의 크기를 반환하는 함수

- SYNOPSIS

  ```c
  size_t	strlcpy(char *dest, const char *src, size_t size)
  ```

- CODE

  ```c
  size_t	count = 0;
  if (!src)
      return (0);
  if (size == 0)
  {
      while (*(src + count))
          count++;
      return (conut);
  }
  while (count < size - 1 && *(src + count))
  {
      *(dest + count) = *(src + count);
      count++;
  }
  if (count < size)
      *(dest + count) = '\0';
  while (*(src + count))
      count++;
  return (count);
  ```
  
- 동작
  1. src 주소가 없으면 0 반환

  2. size가 0이면, src의 길이 반환

  3. count가 size - 1보다 작고 (널값 고려) src + count 에 값이 있으면 반복
  
     3-1) dest + count 번째에 src + count 번째 값 대입
  
     3-2) count 값 증가
  
  4. count가 size보다 작으면 dest + count 번째에 널값 대입.
  
  5. src + count값이 남아있을 때까지 count 값 증가
  
  6. count 반환
  