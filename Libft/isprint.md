## isprint

- 매개변수로 들어오는 값이 출력 가능한 값인지 판별해주는 함수

- SYNOPSIS

  ```c
  int	isprint(int c)
  ```

- CODE

  ```c
  if (c >= 32 && c <= 126)
      return (1);
  else
      return (0);
  ```
  
- 동작
  1. 매개변수 c가 ascii code 32와 126 사이에 있는 값(출력 가능)일 경우 __1__ 반환.
2. 매개변수 c가 ascii code 32와 126 사이에 있지 않은 값(출력 불가)일 경우 __0__ 반환.