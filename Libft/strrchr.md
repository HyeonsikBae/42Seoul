## strrchr

- 문자열 str의 뒤에서부터 문자 c를 찾아 그 위치를 반환하는 함수

- SYNOPSIS

  ```c
  char	*strrchr(const char *str, int c)
  ```

- CODE

  ```c
  {
  	int     count = 0;
  	while (*(str + count))
  		count++;
  	while (count >= 0)
  	{
  		if (*(str + count) == (char)c)
  			return (str + count);
  		count--;
  	}
  	return (NULL);
  }
  ```
  
- 동작
  1. 문자열 마지막 값을 정수 count에 저장.

  2. count 값이 0 이상이면 반복

     2-1. str의 count 번째 값이 c와 같으면 해당 위치 반환
  
     2-2. count 값 감소
  
  3. count 값 모두 탐색할 경우 NULL 반환
  