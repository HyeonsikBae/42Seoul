## lstadd_front

- Linked List의 맨 앞에 새로운 요소를 추가하는 함수

- SYNOPSIS

  ```c
  void lstadd_front(t_list **lst, t_list *new)
  ```

- CODE

  ```c
  {
  	if (!lst || !new)
  		return ;
  	new->next = *lst;
  	*lst = new;
  }
  ```
  
- 동작
  1. lst나 new가 비어있으면 함수 종료
2. new 요소의 next에 lst의 주소를 대입
  3. lst의 첫 주소에 new 대입