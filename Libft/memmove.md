## memset

- src의 메모리를 num만큼 dest에 옮기는 함수

- SYNOPSIS

  ```c
  void	*memmove(void *dest, const void *src, size_t num)
  ```

- CODE

  ```c
  unsigned char	*cast_dest = (unsigned char*)dest;
  unsigned char	*cast_src = (unsigned char*)src;
  size_t			count;
  
  if (dest == src)
      return (dest);
  if (src < dest)
  {
      count = num;
      while (count-- > 0)
          *(cast_dest + count) = *(cast_src + count);
  }
  else
  {
      count = 0;
      while (count++ < num)
          *cast_dest++ = *cast_src++;
  }
  return (dest);
  ```
  
- 동작
  1. dest와 src가 같으면 dest 반환.

  2. src의 주소값보다 dest의 주소값이 크면

     2-1) count 에 num 대입.
  
     2-2) count가 0보다 크면 반복
  
     ​	2-2-1) dest의 count번째에 src의 count번째 대입.
  
  3. src 주소값이 dest 주소값보다 크지 않으면
  
     3-1) count 에 0 대입.
  
     3-2) count가 num보다 작으면 반복
  
     ​	3-2-1) dest에 src 대입.
  
  4. dest 반환
  
- 기타

  - 위 코드는 주소값의 대, 소를 비교하여 값 대입순서가 다르다.

    앞부터 값을 대입하는 코드를 짜다 에러가 났는데, 아래와 같은 상황에 에러가 발생했다.

    - char *string = "1234567890";

      char *dest = string + 2;

      char *src = string + 5;

    주소가 겹치는 경우에 대비해 위와 같이 두 가지 조건에 따라 나누어 놓았다.