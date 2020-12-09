## substr

- 문자열 s의 start 번째 인덱스부터 시작하는 크기 len의 문자열을 반환하는 함수

- SYNOPSIS

  ```c
  char	*substr(char const *s, unsigned int start, size_t len)
  ```

- CODE

  ```c
  {
  	char	*result;
  	unsigned int	num = 0;
  
  	if (s == NULL)
  		return (NULL);
  	if (!(result = (char*)malloc(sizeof(char) * (len + 1))))
  		return (NULL);
  	if (ft_strlen(s) <= start)
  	{
  		*result = '\0';
  		return (result);
  	}
  	while (num < len)
  	{
  		*(result + num) = *(s + start + num);
  		num++;
  	}
  	*(result + num) = '\0';
  	return (result);
  }
  ```

- 동작
  1. 문자열 s의 주소값이 비어있으면 NULL 반환

  2. char 형 포인터 변수 result에 len + 1 만큼의 메모리 할당

  3. s의 길이가 start 보다 작으면 result에 NULL 대입 및 result 반환

  4. num이 len보다 작으면 반복

     4-1. result의 num 번째 인덱스에 s의 start + num 번째 값 대입

  5. result의 마지막에 null값 대입
  
  6. result 반환