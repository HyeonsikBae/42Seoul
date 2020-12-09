## lstmap

- Linked List의 모든 요소에 함수 f를 적용하는 함수.

- SYNOPSIS

  ```c
  t_list  *ft_lstmap(t_list *lst, void *(*f)(void *), void (*del)(void *))
  ```

- CODE

  ```c
  {
  	t_list  *new, *node;
  	new = NULL;
  	if (!lst)
  		return (NULL);
  	while (lst)
  	{
  		if (!(node = ft_lstnew(f(lst->content))))
  		{
  			ft_lstclear(&lst, del);
  			ft_lstclear(&new, del);
  			return (NULL);
  		}
  		ft_lstadd_back(&new, node);
  		lst = lst->next;
  	}
  	return (new);
  }
  ```
  
- 동작
  
  1. lst가 비어있으면 NULL 반환
  
  2. lst의 값이 있으면 반복
  
     2-1. lst의 content에 함수 f 를 적용한 새로운 lst를 node에 저장.
  
     ​	2-1-1. 예외사항 발생 시 lst, new 리스트들을 clear하고 NULL 반환
  
     2-2. new 리스트의 뒤에 node 추가
  
     2-3. lst를 다음 lst로 이동
  
  3. new 리스트 반환