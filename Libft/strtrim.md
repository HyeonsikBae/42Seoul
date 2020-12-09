## strtrim

- 문자열 s1 에서 앞, 뒤에 문자열 set을 자른 문자열을 반환하는 함수

- SYNOPSIS

  ```c
  char	*strtrim(char const *s1, char const *set)
  ```

- CODE

  ```c
  {
  	char	*str;
  	int		start, end, i;
  
  	i = 0;
  	start = 0;
  	if (s1 == NULL || set == NULL)
  		return (NULL);
  	end = ft_strlen(s1);
  	while (s1[start] && ft_setcheck(s1[start], set))
  		start++;
  	while (end > start && ft_setcheck(s1[end - 1], set))
  		end--;
  	if (!(str = (char *)malloc(sizeof(char) * (end - start + 1))))
  		return (NULL);
  	while (start < end)
  		str[i++] = s1[start++];
  	str[i] = '\0';
  	return (str);
  }
  ```
  
- 동작

  1. s1, set 값이 비어있으면 NULL 반환
  2. s1 의 앞부터 set 값이 없을 때까지 start 증가
  3. s1 의 뒤부터 set 값이 없을 때까지 end 감소
  4. 문자열 str 에 end - start + 1 만큼의 메모리 할당
  5. start부터 end 까지 값 복사
  6. str의 마지막 값에 NULL 대입
  7. str 반환

  

- ft_setcheck function
  
  ```c
  int		ft_setcheck(char c, char const *set)
  {
  	int	i = 0;
  	while (set[i])
  	{
          if (set[i] == c)
              return (1);
          i++;
  	}
  	return (0);
  }
  ```
  
- 동작
  
  1. 문자 c 값이 문자열 set 값에 포함된 값이면 1 반환
  2. 문자 c 값이 문자열 set 값에 포함되지 않으면 0 반환