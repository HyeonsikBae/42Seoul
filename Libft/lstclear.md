## lstclear

- Linked List를 모두 삭제하고 메모리를 해제하는 함수

- SYNOPSIS

  ```c
  void    ft_lstclear(t_list **lst, void (*del)(void *))
  ```

- CODE

  ```c
  {
  	t_list  *temp;
  	if (!lst)
  		return ;
  	while (*lst)
  	{
  		del((*lst)->content);
  		temp = *lst;
  		*lst = temp->next;
  		free(temp);
  	}
  	free(*lst);
  }
  ```
  
- 동작
  
  1. lst가 비어있으면 함수 종료
  
  2. lst내 값이 존재하면 반복
  
     2-1. lst의 content에 매개변수로 주어진 del 함수 적용
  
     2-2. temp에 lst대입
  
     2-3. lst에 temp의 다음 주소 대입
  
     2-4. temp 메모리 해제
  
  3. lst 메모리 해제