## lstnew

- Linked list 의 새로운 노드를 선언하는 함수

- SYNOPSIS

  ```c
  t_list	*ft_lstnew(void *content)
  ```

- CODE

  ```c
  t_list	*new;
  
  if (!(new = (t_list*)malloc(sizeof(t_list))))
      return (NULL);
  new->content = content;
  new->next = NULL;
  return (new);
  ```
  
- 동작
  
  1. t_list 타입의 포인터형 변수 new 선언
  2. new에 t_list 크기의 메모리 할당 및 실패 시 NULL 반환
  3. 구조체 변수 new의 멤버변수 content에 파라미터로 들어온 content 대입.
  4. 구조체 변수 new의 멤버변수 next에 NULL 대입.
  5. new 반환