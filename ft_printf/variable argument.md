## variable argument

인자의 개수가 변한다는 의미.

stdarg.h 에 포함되어 있으며, 헤더 내의 함수들을 통해 가변 인자를 활용할 수 있다.

대표적으로 printf 가 가변 인자를 활용하는 함수이다.

가변 인자를 받는 함수는 꼭 1개의 고정 인자가 필요하다.

### stdarg.h

- va_list

  가변 인자를 담을 공간을 선언하기 위한 자료형

  ```c
  va_list	ap;
  ```

- va_start

  가변인자의 리스트를 초기화하는 함수.

  ```c
  va_start(ap, first argument);
  ```

- va_end

  가변인자의 리스트 사용을 끝내는 함수.

  ```c
  va_end(ap);
  ```

- va_arg

  가변인자 리스트의 ap 포인터가 위치한 부분을 읽어오는 함수

  ap 포인터를 타입의 길이만큼 뒤로 옮기기 때문에 다음 값을 이어서 읽어올 수 있다.

  데이터를 파라미터로 입력하는 type으로 읽어들인다.

  ```c
  va_arg(ap, type)
  ```