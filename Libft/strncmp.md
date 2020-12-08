## strncmp

- 두 문자열을 n 만큼 비교하여 그 차이를 반환하는 함수

- SYNOPSIS

  ```c
  int	strncmp(const char *str1, const char *str2, size_t count)
  ```

- CODE

  ```c
  {
  	size_t	i = 0;
  	unsigned char   *s1, *s2;
  
  	s1 = (unsigned char*)string1;
  	s2 = (unsigned char*)string2;
  	if (s1 == s2 || count == 0)
  		return (0);
  	while (i < count - 1
             && *(s1 + i) != '\0'
             && *(s2 + i) != '\0'
             && *(s1 + i) == *(s2 + i))
  		i++;
  	return (*(s1 + i) - *(s2 + i));
  }
  ```
  
- 동작
  1. s1 과 s2가 같거나, 비교할 길이가 0 이면 0 반환

  2. 두 값이 같으면 반복

     2-1. i 값 증가하여 다음 인덱스 탐색
  
  3. 두 값의 차이 반환
  