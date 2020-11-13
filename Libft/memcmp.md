## memcmp

- 두 메모리를 number 만큼 비교하는 함수

- SYNOPSIS

  ```c
  int memcmp(const void *pointer1, const void *pointer2, size_t number)
  ```

- CODE

  ```c
  size_t			count;
  unsigned char	*p1;
  unsigned char	*p2;
  
  p1 = (unsigned char*)pointer1;
  p2 = (unsigned char*)pointer2;
  if (p1 == p2 || number == 0)
  	return (0);
  count = 0;
  while (count < number)
  {
      if (*(p1 + count) != *(p2 + count))
          return (*(p1 + count) - *(p2 + count));
      count++;
  }
  return (0);
  ```

- 동작
  1. void 포인터 타입의 값을 unsigned char 포인터 값으로 casting

  2. 비교하려는 두 매개변수가 동일하거나, 비교할 사이즈가 0이면 __0__ 반환.

  3. number만큼 반복

     3-1) 비교하려는 두 매개변수가 같지 않으면 __두 변수의 차__ 반환.

     3-2) 같으면 다음 주소의 값 비교를 위해 count 값 증가

  4. 모든 값이 같아 반복문을 탈출하면 __0__ 반환.