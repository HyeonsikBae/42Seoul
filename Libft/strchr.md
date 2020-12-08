## strchr

- 문자열 str에서 문자 c를 찾아 그 위치를 반환하는 함수

- SYNOPSIS

  ```c
  char	*strchr(const char *str, int c)
  ```

- CODE

  ```c
  {
  	while (*str != (char)c)
  	{
  		if (*str == '\0')
  			return (NULL);
  		str++;
  	}
  	return ((char*)str);
  }
  ```
  
- 동작
  1. str의 값이 c와 같지 않으면 반복

     1-1. str 값이 NULL 이면, NULL 반환

     1-2. str 값 증가.
  
  2. c와 같은 값을 가진 str 반환
  