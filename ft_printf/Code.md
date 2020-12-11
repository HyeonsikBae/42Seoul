# Code

- synopsis

  ```c
  int	ft_printf(const char *format, ...)	
  ```

- 구조체

  ```c
  typedef struct	s_print
  {
  	va_list		ap;			//variable argument 사용을 위한 변수
  	char		*str;		//format 을 담아놓을 변수
  	int			flag[4];	//'-' flag, '0' flag, width, precision 유무 저장
  	long		precision;	//precision 값 저장
  	long		width;		//width 값 저장
  	int			size_pre;	//width 값으로 인한 선행 값 저장
  	int			size_post;	//precision 값으로 인한 선행 값 저장
  	int			sign;		//부호 저장
  	int			idx;		//str을 순차적으로 탐색하기 위한 인덱스 값
  	int			rtn;		//출력 개수를 저장하여 리턴하기 위한 변수
  }				t_print;
  ```

---

- ft_printf

  ```c
  t_print *print;
  int		rtn;
  
  if (!(print = (t_print*)malloc(sizeof(t_print))))
      return (-1);
  print->rtn = 0;
  if (format){
      print = init(print, format, 0);
      va_start(print->ap, format);
      ft_check_format(print);
      va_end(print->ap);
  }
  rtn = print->rtn;
  free(print->str);
  free(print);
  return (rtn);
  ```

  - format 에 값이 있으면, flag 0 과 함께 초기화 한 다음 check_format 함수로 넘어간다.
  - check_format 내부에서 출력이 모두 이루어지며, 이를 끝낸 후엔 rtn 값을 반환한다.

  

- initialization

  ```c
  t_print	*init(t_print *print, const char *str, int flag)
  {
  	if (flag == 0)
  	{
  		print->str = ft_strdup(str);
  		print->idx = 0;
  	}
  	/*
  	나머지 구조체 멤버변수 초기화
  	*/
  }
  ```

  - flag를 통해 맨 처음 초기화부분과 check_format 내부에서 구조체가 사용되던 중간 초기화하는 부분을 나눈다.
  - 맨 처음에만 format의 값을 가져오고 인덱스를 초기화한다.

  

- check_format

  ```c
  while (print->str[print->idx])
  {
  	if (print->str[print->idx] == '%')
      {
          print = init(print, "42", 42);
          print->idx += 1;
          check_specification(print);
      }
      else
      {
          ft_write(print->str[print->idx], print);
          print->idx += 1;
      }
      return ;
  }
  ```

  - str 값을 전부 탐색한다.
  - % 가 나온다는 것은 specification 이 나온다는 의미이므로 구조체를 초기화하고 다음 인덱스부터 check_specification 함수로 넘어간다.
  - % 가 나오지 않으면 문자를 하나 출력하고 다음 인덱스로 넘어간다.

  

- check_specification

  ```c
  check_flag(print);
  check_width(print);
  check_precision(print);
  check_type(print);
  // 세부 코드 생략
  ```

  - '-', '0' flag의 유무를 판별하여 구조체에 결과를 저장한다.
  - width의 유무를 판별하고, 결과와 값을 구조체에 저장한다.
  - precision의 유무를 판별하고, 결과와 값을 구조체에 저장한다.
  - type을 체크하고 각 type에 맞는 출력함수로 넘어간다.

  

- print

  - d, i, u, x, X, c, s, p, % type에 대하여 각각의 조건에 맞춰 출력을 한다.

    ```c
    // 대표적으로 정수에 대한 코드만 수록
    if (/*d type*/)
        va_arg(print->ap, int);
    else
        va_arg(print->ap, unsigned int);
    set_precision;		// precision 으로 인해 나타나는 선행 값 저장
    set_width;			// width로 인해 나타나는 선행 값 저장
    print_integer;		// 각 옵션들의 유무에 따라 부호, 선행 값, 출력 값 등을 순서에 맞춰 출력
    ```

  - 출력이 이루어질 때마다 구조체의 rtn 값을 증가시켜 후에 출력 개수를 확인할 수 있도록 한다.