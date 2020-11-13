## tolower

- 매개변수로 들어오는 값이 대문자이면 소문자로 변환해주는 함수

- SYNOPSIS

  ```c
  int	tolower(int c)
  ```

- CODE

  ```c
  if (c >= 'A' && c <= 'Z')
      c += 32;
  return (c);
  ```
  
- 동작
  1. 매개변수 c가 A와 Z 사이에 있는 값일 경우

     1-1) 매개변수 c에 32 합산. (ascii code 상 소문자와 대문자의 차이만큼 합산.)

  2. __c 값__ 반환