## itoa

- int형 정수를 char형 포인터로 변환하여 반환하는 함수

- SYNOPSIS

  ```c
  char	*itoa(int n)
  ```

- CODE

  ```c
  int		sign = (n < 0) ? -1 : 1;
  long	abs = long(n) * sign;
  int		size = check_size_itoa(abs, sign);
  char	*result;
  
  if (!(result = malloc(sizeof(char) * (size + 1))))
      return (NULL);
  result = convert(result, abs, size, sign);
  return (result);
  ```
  
- 동작
  1. n의 양수, 음수를 판단하여 sign에 부호 저장
2. int 타입의 최소, 최대치의 경우를 고려하여 long타입으로 캐스팅힌 절대값을 abs에 저장
  3. 부호를 고려하여 변환할 문자의 수를 size에 저장
  4. result에 size + 1만큼 메모리 할당 및 실패 시 Early return.
  5. converting 함수 실행
  6. result 반환.

- check_size_itoa CODE

  ```c
  int		size = 0;
  if (n == 0)
  	return (1);
  while (n > 0)
  {
      size++;
      n /= 10;
  }
  if (sign == -1)
      return (size + 1);
  else
      return (size);
  ```

- 동작

  1. n 값이 0이면 1 반환.

  2. n이 0보다 크면 반복

     2 - 1) 사이즈 증가

     2 - 2) n에 n을 10으로 나눈 값 대입

  3. sign 이 -1 이면 size + 1반환

  4. sign 이 1 이면 size 반환

- convert CODE

  ```c
  *(result + size--) = '\0';
  if (n == 0)
  {
      *(result + size) = '0';
      return (result);
  }
  while (size >= 0 && n > 0)
  {
      *(result + size--) = n % 10 + '0';
      n /= 10;
  }
  if (sign == -1)
      *(result + size) = '-';
  return (result);
  ```

- 동작

  1. result의 size 번째 주소의 값에 널 저장 및 size 감소.

  2. n 이 0이면 result의 size번째 주소의 값에 '0' 저장 및 반환

  3. size가 0보다 크거나 같고, n이 0보다 크면 반복

     3 - 1) result의 size 번째 주소의 값에 n % 10 값을 char형으로 변환시켜 저장 및 size 감소.

     3 - 2) n값에 n / 10 값 저장.

  4. sign 값이 -1 이면 result의 size 번째 주소의 값에 '-' 저장.

  5. result 반환.