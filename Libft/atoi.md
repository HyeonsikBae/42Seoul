## atoi

- 매개변수로 들어오는 문자열을 정수로 변환시켜주는 함수

- SYNOPSIS

  ```c
  int	atoi(const char *string)
  ```

- CODE

  ```c
  long	count;
  long	result;
  int		sign;
  
  count = 0;
  while (string[count] == ' ' || (string[count] >= 9 && string[count] <= 13))
      count++;
  sign = 1;
  if (*(string + count) == '+' || *(string + count) == '-')
  {
      sign = check_sign(string, count);
      count++;
  }
  result = 0;
  while (*(string + count) >= '0' && *(string + count) <= '9')
  {
      if (result * sign > 2147483647)
          return (-1);
      if (result * sign < -2147483648)
          return (0);
      result = result * 10 + (*(string + count) - '0');
      count++;
  }
  result *= sign;
  return ((int)result);
  ```
  
- CODE_sub

  - check_sign
    - string의 count번째 값이 '-'이면 -1을, 그렇지 않으면 1을 반환해주는 함수.
    - atoi 함수에 매개변수로 들어오는 string의 부호를 판단하기 위해 작성한 함수.

  ```c
  int	check_sign(const char *string, long count)
  {
      int	sign;
      
      sign = 1;
      if (*(string + count) == '-')
          sign *= -1;
      return (sign);
  }
  ```

- 동작

  1. string의 isspace값 판별 후 index 이동.

  2. string의 부호 판별 후 index 이동 및 부호값 저장.

  3. string의 값이 숫자이면 반환.

     3-1) 결과값이 INT_MAX 보다 크면 __-1__ 반환

     3-2) 결과값이 INT_MIN 보다 작으면 __0__ 반환

     3-3) 결과값에 반환값 * 10 + string의 해당 인덱스값 대입. (문자열의 앞부터 정수로 변환하기 때문에 자릿값을 위해 기존 반환값에 10씩 곱해가며 합산.)

     3-4) 인덱스를 체크할 count 값 증가

  4. 결과값에 부호값 곱셈.
  5. __int형으로 캐스팅된 결과값__ 반환

- 기타

  - 처음 코드를 작성했을 때, INT_MAX, INT_MIN 값의 범위를 넘어가는 경우에 대해 처리하지 못했다.

    이를 처리하기 위해 적용한 방법은 다음과 같다.

    - 결과값을 담을 변수를 long 타입으로 지정
    - 결과값에 새로운 값을 담을 때마다 INT_MAX, INT_MIN 값의 범위를 넘어가는지 확인