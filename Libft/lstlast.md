## lstlast

- 매개변수로 들어오는 Linked List의 마지막 list의 주소를 반환해주는 함수

- SYNOPSIS

  ```c
  t_list	*lstlast(t_list *list)
  ```

- CODE

  ```c
  if (!list)
      return (NULL);
  while (42)
  {
      if (list->next)
          list = list->next;
      else
          return (list);
  }
  ```
  
- 동작
  
  1. 매개변수로 주어진 list의 주소값이 없을 경우 __NULL__ 반환.
  
  2. 반복
  
     2-1) list의 다음 주소값이 있으면 list에 다음 주소값 대입
  
     2-2) list의 다음 주소값이 없으면 __list__ 반환