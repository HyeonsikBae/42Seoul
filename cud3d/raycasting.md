# raycasting

---

raycasting 이란 2D 지도를 활용하여 3D를 렌더링하는 기술이다.

좀 더 자세히 말하면 실제 3D 엔진을 사용하지 않고, 2D 맵을 통해 3D처럼 보이게끔 하는 기술이다.

아래와 같은 지도가 있다고 가정해보자.

![example_map](https://github.com/HyeonsikBae/42Seoul/blob/master/cud3d/raycasting_map_example.png)

player의 시야각이 60도인 상황에서, 6도마다 10번의 시야를 확인해보면 각 시야는 거리가 다르다는 것을 알 수 있다.

이 시야의 거리로 플레이어가 바라보는 지점의 원근감을 확인할 수 있다.

이 시야각을 raycasting을 통한 rendering 화면을 출력할 해상도의 너비로 나누고, 원근감을 출력할 해상도의 높이의 비율에 대입한다면 2D map을 통한 3D 화면을 출력할 수 있다.