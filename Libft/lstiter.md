## lstiter

- Linked List의 모든 요소에 함수 f를 적용하는 함수

- SYNOPSIS

  ```c
  void lstiter(t_list *lst, void (*f)(void*))
  ```

- CODE

  ```c
  if (!lst)
      return ;
  while (lst)
  {
      f(lst->content);
      lst = lst->next;
  }
  ```

- 동작
  1. Linked List의 주소값이 없으면 Early return

  2. Linked List의 값이 있으면 반복

     2-1) list의 content에 arrow operator로 접근하여 f 함수 적용

     2-2) list의 next에 arrow operator로 접근하여 list의 주소를 다음 list의 주소로 대입