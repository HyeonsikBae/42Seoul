## strlcat

- dest 함수에 src를 붙여주고, 그 길이를 반환하는 함수

- SYNOPSIS

  ```c
  size_t	strlcat(char *dest, const char *src, size_t size)
  ```

- CODE

  ```c
  size_t  count, dest_len, src_len;
  
  dest_len = ft_strlen(dest);
  src_len = ft_strlen(src);
  if (size <= dest_len)
  	return (src_len + size);
  count = 0;
  while (count + dest_len + 1 < size && *(src + count))
  {
  	*(dest + dest_len + count) = *(src + count);
  	count++;
  }
  *(dest + dest_len + count) = '\0';
  return (src_len + dest_len);
  ```
  
- 동작
  1. dest의 길이가 size 이상이면 **src 길이 + size 값** 반환

  2. dest의 길이 + 1 이 size보다 작고, src 값이 존재하면 반복

     2-1. dest의 뒤에 src 값 붙이기.
  
  3. dest의 마지막 값에 null 대입.
  
  4. dest + src 의 길이 반환
  