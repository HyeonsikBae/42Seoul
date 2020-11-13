## isdigit

- 들어오는 매개 변수가 숫자인지 아닌지를 판별하는 함수

- SYNOPSIS

  ```c
  int	isdigit(int c)
  ```

- CODE

  ```c
  if (c >= '0' && c <= '9')
      return (1);
  else
      return (0);
  ```

- 동작
  1. 매개변수 c가 숫자이면 1 반환

  2. 매개변수 c가 숫자가 아니면 0 반환