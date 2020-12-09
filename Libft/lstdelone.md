## lstdelone

- Linked List의 content를 삭제하고 메모리를 해제하는 함수

- SYNOPSIS

  ```c
  void    lstdelone(t_list *lst, void (*del)(void *))
  ```

- CODE

  ```c
  {
  	del(lst->content);
  	free(lst);
  }
  ```
  
- 동작
  
  1. 매개변수로 주어진 del 함수를 lst의 content에 적용
  2. lst 해제