## lstadd_back

- Linked List의 맨 뒤에 새로운 요소를 추가하는 함수

- SYNOPSIS

  ```c
  void lstadd_back(t_list **lst, t_list *new)
  ```

- CODE

  ```c
  {
  	t_list  *last;
  	if (!new)
  		return ;
  	if (!*lst)
  		*lst = new;
  	else
  	{
  		last = ft_lstlast(*lst);
  		last->next = new;
  	}
  }
  ```
  
- 동작
  
  1. new가 비어있으면 함수 종료
  2. lst의 첫 주소가 비어있으면 첫 주소에 new 대입
  3. lst의 첫 주소가 비어있지 않으면 마지막 주소로 이동 후, next에 new 요소 대입