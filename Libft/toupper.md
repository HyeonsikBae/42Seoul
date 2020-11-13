## toupper

- 매개변수로 들어오는 값이 소문자이면 대문자로 변환해주는 함수

- SYNOPSIS

  ```c
  int	toupper(int c)
  ```

- CODE

  ```c
  if (c >= 'ㅁ' && c <= 'ㅋ')
      c -= 32;
  return (c);
  ```
  
- 동작
  1. 매개변수 c가 A와 Z 사이에 있는 값일 경우

     1-1) 매개변수 c에 32 감산. (ascii code 상 소문자와 대문자의 차이만큼 감산.)

  2. __c 값__ 반환