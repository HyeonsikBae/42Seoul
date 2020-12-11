## printf

stdio.h 에 포함되어 있으며 여러 타입의 데이터를 각 서식에 맞춰 출력해주는 I/O 함수

출력되는 문자의 수를 int 타입으로 반환한다.

printf 의 f 는 formatted의 약자로, 서식화된 출력을 지원한다는 의미이다.

### printf 함수

- 함수 원형

  ```c
  int	printf(const char *restrict format, ...);
  ```

  가변 인자 함수로써, restrict format 외에 뒤에 들어오는 모든 인자를 받을 수 있다.

  뒤에 들어오는 인자 (...에 해당하는 부분)에는 restrict format에서 format tag 에 따라 출력할 문자가 들어오게 된다.

  

- parameter

  - restrict format
    - 출력할 문자열이 들어온다.
    - format tag가 들어오면 각 format tag를 출력하기 위한 인자가 추가로 들어오게 된다.
  - ...
    
    - format tag에 맞는 타입의 문자가 들어온다.
    
      

- format tag

  ```c
  %[flag][width][precision][length]type
  ```

  restrict format에 입력할 수 있는 format flag로, 어떤 값이 들어오는가에 따라 출력할 결과가 바뀌게 된다.

  - flag

    | flag    | description                                     | default                 |
    | ------- | ----------------------------------------------- | ----------------------- |
    | -       | 좌측 정렬                                       | 우측 정렬               |
    | +       | 정수 타입에 부호 추가                           | 음수의 경우만 부호 추가 |
    | 0       | width가 있을 경우, 남는 칸 0 출력               | 남는 칸 space 처리      |
    | (space) | 부호가 있고, 양수인 경우 출력 값 앞에 공백 출력 | no blank                |
    | #       | x 플래그의 경우, 0x (0X) 를 앞에 출력한         | no blank                |

  - width

    | width  | description                                                  |
    | ------ | ------------------------------------------------------------ |
    | number | 최소 출력할 문자 수.<br />인쇄 할 값이 number보다 짧으면 선행 공백으로 채워진다.<br />인쇄 할 값이 number보다 길면 인쇄 할 값이 잘리지 않는다. |
    | *      | 최소 출력할 문자 수를 다음 가변 인자에서 받는다.<br />number와 동일하게 적용된다. |

  - precision

    | precision | description                                                  |
    | --------- | ------------------------------------------------------------ |
    | .number   | 최소 기록할 문자 수.<br />기록 할 값이 number보다 짧으면 선행 0으로 채워진다.<br />기록 할 값이 number보다 길면 기록 할 값이 잘리지 않는다. |
    | .*        | 최소 기록할 문자 수를 다음 가변 인자에서 받는다.<br />.number와 동일하게 적용된다. |

  - length

    | length | d i           | u o x X                | f F e E g G a A | c      | s         | p      | n               |
    | ------ | ------------- | ---------------------- | --------------- | ------ | --------- | ------ | --------------- |
    | (none) | int           | unsigned int           | double          | int    | char *    | void * | int *           |
    | hh     | signed int    | unsigned char          |                 |        |           |        | signed char *   |
    | h      | short int     | unsigned short int     |                 |        |           |        | short int *     |
    | l      | long int      | unsigned long int      |                 | wint_t | wchar_t * |        | long int *      |
    | ll     | long long int | unsigned long long int |                 |        |           |        | long long int * |
    | j      | intmax_t      | uintmax_t              |                 |        |           |        | intmax_t *      |
    | z      | size_t        | size_t                 |                 |        |           |        | size_t *        |
    | t      | ptrdiff_t     | ptrdiff_t              |                 |        |           |        | ptrdiff_t *     |
    | L      |               |                        | long double     |        |           |        |                 |

  - type

    | type | description                           |
    | ---- | ------------------------------------- |
    | d    | 부호가 있는 10진수 정수               |
    | i    | 부호가 있는 10진수 정수               |
    | u    | 부호가 없는 10진수 정수               |
    | o    | 부호가 없는 8진수 정수                |
    | x    | 부호가 없는 16진수 정수 (소문자 표기) |
    | X    | 부호가 없는 16진수 정수 (대문자 표기) |
    | f    | 10진수 실수 (소문자 표기)             |
    | F    | 10진수 실수 (대문자 표기)             |
    | e    | 지수 (소문자 표기)                    |
    | E    | 지수 (대문자 표기)                    |
    | g    | e 와 f 중 짧은 표기 사용              |
    | G    | E 와 F 중 짧은 표기 사용              |
    | a    | 16진수 실수 (소문자 표기)             |
    | A    | 16진수 실수 (대문자 표기)             |
    | c    | 문자                                  |
    | s    | 문자열                                |
    | p    | 포인터 주소                           |
    | n    | Nothing printed                       |
    | %    | %                                     |
    
    

- escape sequence

  | escape sequence | description |
  | --------------- | ----------- |
  | \\'             | 작은 따옴표 |
  | \\"             | 큰 따옴표   |
  | \?              | 물음표      |
  | \\\             | 백슬래시    |
  | \a              | 경고음 발생 |
  | \b              | 백스페이스  |
  | \n              | 개행        |
  | \r              | 캐리지 리턴 |
  | \t              | 수평 탭     |
  | \v              | 수직 탭     |
  | \f              | 폼 피드     |
