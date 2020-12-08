## strdup

- 문자열 s를 복사한 문자열을 반환하는 함수

- SYNOPSIS

  ```c
  char	*strdup(const char *s)
  ```

- CODE

  ```c
  {
  	char	*result;
  	int		s_len = 0;
  
  	if (!(result = (char*)malloc(sizeof(char) * (ft_strlen(s) + 1))))
  		return (NULL);
  	while (*(s + s_len))
  	{
  		*(result + s_len) = *(s + s_len);
  		s_len++;
  	}
  	*(result + s_len) = '\0';
  	return (result);
  }
  ```
  
- 동작
  
  1. s 크기의 문자형 포인터 변수 result 생성
  2. result 에 s 값 복사
  3. result 의 마지막에 null 값 대입
  4. result 반환