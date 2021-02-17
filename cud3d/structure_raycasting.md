# raycasting

---

cub3d는 앞서 설명한대로 2D map을 활용하여 3D처럼 보이는 화면을 만들어주는 기술이다.

우리는 플레이어의 시야를 해상도의 너비 수만큼 나누어 시야를 표현할 수 있다.

각 시야에서 플레이어의 위치로부터 플레이어가 바라보는 벽의 위치까지의 거리를 통해 원근감을 나타낼 수 있다.

해상도 너비 수 만큼 레이캐스팅 벡터를 구해서 DDA 알고리즘을 실행하면 이 거리를 구할 수 있다.

해상도 너비 수만큼 나눠진 레이캐스팅 벡터는 다음과 같이 구할 수 있다.

![player_sight](https://github.com/HyeonsikBae/42Seoul/blob/master/cud3d/player_sight.png)

```c
for(int i = 0; i < resolution_x; i++)
{
	raycasting_range = 2 * i / resolution_x - 1;
    raycasting_vector_x = player_sight_x + player_screen_x * raycasting_range;
    raycasting_vector_y = player_sight_y + player_screen_y * raycasting_range;
}
```



레이캐스팅 벡터를 통해 x절편의 벽에 부딪히는 dda와 y절편의 벽에 부딪히는 dda를 실행한다.

각 dda를 통해 벽까지의 거리를 반환받고, 이 중 짧은 거리를 통해 3D를 표현하게 된다.

```c
double	distance_x = dda_x(raycasting_vector_x, raycasting_vector_y);
double	distance_y = dda_y(raycasting_vector_x, raycasting_vector_y);
double	distance = (distance_x > distance_y ? distance_y : distance_x);
draw_raycasting(distance);
```



3D 표현을 위해 화면을 그릴 때는 해상도 높이 수만큼 반복하며 천장, 벽, 바닥을 그린다.

이 때, 텍스쳐를 벽에 그리기 위해 텍스쳐 크기 : 벽의 크기 비율에 맞는 텍스처 내부 색상값을 가져온다.

```c
for(int i = 0; i < resolution_y; i++)
{
	if (i == pos_floor)
		draw_floor_color;
	else if (i == pos_ceiling)
		draw_ceiling_color;
	else
		draw_wall;	//텍스처와 벽의 비율에 맞춰 해당 텍스쳐 값 대입.
}
```

