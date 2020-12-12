# MiniLibx - Drawing inside windows

---

MiniLibs 의 Drawing inside windows 파트엔 2가지의 함수가 구현되어 있다.

아래 두 함수는 window 밖의 모든 디스플레이를 폐기하므로 기능구현이 굉장히 느리다.

manual에서도 아래 기능 대신 이미지 사용을 권장한다.

- mlx_pixel_put

  - description

    윈도우의 특정 좌표에 특정 색으로 하나의 픽셀을 채우는 함수

  - synopsys

    ```c
    int	mlx_pixel_put(void *mlx_ptr, void *win_ptr, int x, int y, int color);
    ```

  - parameter

    void *mlx_ptr : connection identifier

    vold *win_ptr : window identifier

    int x : 윈도우의 x 좌표

    int y : 윈도우의 y 좌표

    - 0, 0 좌표는 윈도우의 맨 왼쪽, 맨 위이다.

    int color : 특정 컬러

    

- mlx_string_put

  - description

    윈도우의 특정 좌표에 특정 색의 문자열을 채우는 함수

  - synopsys

    ```c
    int	mlx_string_put(void *mlx_ptr, void *win_ptr, int x, int y, int color, char *string);
    ```

  - parameter

    void *mlx_ptr : connection identifier

    vold *win_ptr : window identifier

    int x : 윈도우의 x 좌표

    int y : 윈도우의 y 좌표

    - 0, 0 좌표는 윈도우의 맨 왼쪽, 맨 위이다.

    int color : 특정 컬러

    char *string : 특정 문자열
