# map validation check

---

cub3d 에서 map은 몇 가지의 규칙을 가진다.

```
1. player 는 한 명일 것.
2. 맵은 벽으로 막혀있을 것.
3. map에 공백으로 처리된 부분은 map의 일부이므로 알아서 처리할 것.
```

이를 위해 DFS를 통해 맵 유효성 검사 기능을 구현하였고, 아래와 같은 동작을 한다.

```
1. player 수를 체크하여 1이 아닌 경우 Error
2. player 위치 및 방향 저장
3. map이 뚫린 경우 Error
```



DFS는 플레이어 위치로부터, 4방향으로 뻗어나가며 검사를 한 공간의 값을 임의로 바꾸어 다시 탐색하지 않게끔 구현하였다.

```c
void		check_map_validation(t_window *window, int x, int y)
{
	if (x 및 y가 가질 수 있는 범위 초과)
        error();
    if (이미 검사한 범위이거나 벽인 경우)
        return ;
    if (통로의 경우)
        통로 값을 임의의 값으로 변경
    if (스프라이트의 경우)
        스프라이트 값을 임의의 값으로 변경
    check_map_validation(window, x - 1, y);
    check_map_validation(window, x + 1, y);
    check_map_validation(window, x, y - 1);
    check_map_validation(window, x, y + 1);
    return ;
}
```

