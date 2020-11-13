## split

- 문자열 s를 문자 c를 기준으로 나눠서 이중포인터에 저장하여 반환하는 함수

- SYNOPSIS

  ```c
  char	**split(char const *s, char c)
  ```

- CODE

  ```c
  char	**result;
  long	block_size;
  
  if (!s)
      return (NULL);
  block_size = ft_check_block_size(s, c);
  if (!(result = (char**)malloc(sizeof(char*) * (block_size + 1))))
      return (NULL);
  result = ft_splitting(result, s, c, block_size);
  return (result);
  ```
  
- 동작
  1. 입력으로 들어오는 문자열 s의 주소가 비어있는 경우 Early return.

  2. 결과를 담을 이중포인터 result 메모리 할당에 실패할 경우 return.

     2 -1) 메모리 할당은 c에 의해 나눠질 블록의 수 + 1 (NULL 고려)만큼 할당한다.
  
  3. split 실행.
  
  4. 결과 반환.
  
  
  
- check_block_size CODE

  ```c
  long	conut = 0;
  long	index = 0;
  
  while (*(s + index))
  {
      if (*(s + index) != c && (*(s + index + 1) == c || *(s + index + 1) == '\0'))
          count++;
      index++;
  }
  return (count);
  ```

- 동작

  1. 문자열 s의 index 번째 주소에 값이 있으면 반복.

     1-1) 해당 값이 c가 아니고, 다음 값이 c거나 NULL이면 count 증가

  2. count 반환.

- 시행 착오

  - count가 증가하는 조건을 *(s + index) != c && *(s + index + 1) == c 로 작성하여 에러가 발생했었다.
  - 마지막 블록은 카운트하기 위해 *(s + index + 1) == '\0'이라는 조건을 추가하여 해결하였다.

- splitting CODE

  ```c
  long	idx = 0;
  long	p = 0;
  long	start = 0;
  
  while (s[p] != '\0' && idx < block_size)
  {
      while (s[p] != '\0' && s[p] == c)
          p++;
      start = p;
      while (s[p] != '\0' && s[p] != c)
          p++;
      if (start != p)
      {
          if (!(result[idx] = (char*)malloc(sizeof(char) * (p - start + 1))))
              return (mem_free(result, idx));
          strlcpy(result[idx], s + start, p - start + 1);
      }
      idx++;
  }
  result[idx] = NULL;
  return (result);
  ```

- 동작

  1. s 의 p번째 주소에 값이 있고, idx 가 block size보다 작으면 반복
     - idx는 이중포인터의 0번째 포인터부터 값을 담기 위한 값으로 block size가 되면 모든 값이 찼다는 것을 의미.
  2. s 의 p번째 주소가 c이면 p를 반복적으로 증가시켜 블록의 시작할 포인터 위치를 찾는다.
  3. s 의 p번재 주소가 c가 아니면 p를 반복적으로 증가시켜 블록의 마지막 포인터 위치를 찾는다.
  4. 시작 포인터와 마지막 포인터가 다르면 해당 idx 번째 포인터에 메모리 할당 후 값을 복사하여 넣는다.
  5. block_size 번째 포인터에는 NULL 값을 담는다.
  6. result를 반환.

- 시행 착오

  - 메모리 할당에 실패했을 경우, NULL을 리턴했었는데 기존에 할당된 메모리를 해제하지 않아 누수 발생.
    - mem_free라는 함수를 만들어서 해결하였다.

- mem_free CODE

  ```c
  long	index = 0;
  
  while (index < block_index)
  {
      free(result[index]);
      index++;
  }
  free(result);
  return (NULL);
  ```

- 동작

  1. index를 메모리 할당에 실패한 block_index까지 반복하며 메모리를 해제한다.
  2. 전체 메모리를 해제한다.
  3. NULL 반환.