## strnstr

- 문자열 big에서 문자열 little과 일치하는 문자열의 위치를 반환하는 함수

- SYNOPSIS

  ```c
  char	*strnstr(char *big, char *little, size_t len)
  ```

- CODE

  ```c
  {
  	size_t  little_len, point1, point2;
  
  	if (!*little)
  		return (big);
  	if (!*big || len == 0)
  		return (NULL);
  	little_len = ft_strlen(little);
  	point1 = 0;
  	while (*(big + point1) && point1 + little_len <= len)
  	{
  		point2 = 0;
  		while (*(big + point1 + point2) == *(little + point2))
  		{
  			if (point2 == little_len - 1)
   				return (big + point1);
  			point2++;
  		}
  		point1++;
  	}
  	return (NULL);
  }
  ```
  
- 동작
  1. little 주소 값이 NULL일 때 big 반환

  2. big 주소 값이 NULL이고, len 값이 0 일 때, NULL 반환

  3. big의 앞부터 반복
  
     3-1. big 값과 little의 값 비교
  
     3-2. big 값에 little 값과 일치하는 값 있으면 해당 값 반환
  
  4. 반복문 모두 돌고 나면 NULL 값 반환
  