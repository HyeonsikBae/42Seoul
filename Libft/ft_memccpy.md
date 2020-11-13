## lstsize

- Linked list 의 길이를 반환하는 함수

- SYNOPSIS

  ```c
  int		ft_lstsize(t_list *lst)
  ```

- CODE

  ```c
  int		count;
  
  if (!lst)
      return (0);
  count = 1;
  while (1)
  {
      if (lst->next)
      {
          count++;
          lst = lst->next;
      }
      else
          break;
  }
  return (count);
  ```
  
- 동작

  1. lst의 주소값이 없으면 0 반환

  2. lst의 다음 주소값이 있으면 반복

     2-1) count 증가

     2-2) lst에 다음 lst의 주소 대입.

  3. lst의 다음 주소가 없으면 반복문 탈출.

  4. count 반환