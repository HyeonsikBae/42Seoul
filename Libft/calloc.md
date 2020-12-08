## calloc

- nmemb 크기의 메모리를 할당하고, 값을 0으로 채워 반환하는 함수

- SYNOPSIS

  ```c
  void	*calloc(size_t nmemb, size_t size)
  ```

- CODE

  ```c
  {
  	void    *mem;
  	size_t  count = 0;
  
  	if (!(mem = malloc(nmemb * size)))
  		return (NULL);
  	while (count < size * nmemb)
  	{
  		*((char*)mem + count) = 0;
  		count++;
  	}
  	return (mem);
  }
  ```
  
- 동작
  
  1. void 형 포인터 mem의 메모리를 nmemb*size 만큼 할당
  2. nmemb*size 까지 0 값 대입.
  3. mem 반환