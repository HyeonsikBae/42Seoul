## strjoin

- 두 문자열을 합친 문자열을 반환하는 함수

- SYNOPSIS

  ```c
  char	*strjoin(char const *s1, char const *s2)
  ```

- CODE

  ```c
  {
  	long    s1_len, s2_len;
  	char    *result;
  
  	if (s1 == NULL || s2 == NULL)
  		return (NULL);
  	s1_len = ft_strlen(s1);
  	s2_len = ft_strlen(s2);
  	if (!(result = (char*)malloc(sizeof(char) * (s1_len + s2_len + 1))))
  		return (NULL);
  	ft_strlcpy(result, s1, s1_len + 1);
  	ft_strlcpy(result + s1_len, s2, s2_len + 1);
  	return (result);
  }
  ```
  
- 동작
  1. s1, s2 중 주소가 NULL 값인 변수가 있으면 NULL 반환
2. result 에 s1 길이 + s2 길이 + 1 만큼의 메모리 할당
  3. result 에 s1 복사
4. result 의 s1 길이 후부터 s2 복사
  5. result 반환