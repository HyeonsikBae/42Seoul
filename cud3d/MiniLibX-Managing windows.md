# MiniLibx - Managing windows

---

MiniLibs 의 Managing windows 파트엔 3가지의 함수가 구현되어 있다.

- mlx_new_window

  - description

    새로운 윈도우를 생성하는 함수이다.

  - synopsys

    ```c
    void *mlx_new_window(void *mlx_ptr, int size_x, int size_y, char *title);
    ```

  - parameter

    void *mlx_ptr : mlx_init의 반환 값으로 connection identifier 이다.

    int size_x : 생성할 윈도우의 가로 사이즈.

    int size_y : 생성할 윈도우의 세로 사이즈.

    char *title : 생성할 윈도우의 타이틀 바에 표시될 제목

  - return

    윈도우 생성에 성공하면 non-null pointer, 실패하면 NULL 을 반환한다.

    반환된 non-null pointer 값은 window identifier 이다.

    

- mlx_clear_window

  - description

    윈도우를 검은색으로 clear하는 함수이다.

  - synopsys

    ```c
    int mlx_clear_window(void *mlx_ptr, void *win_ptr);
    ```

  - parameter

    void *mlx_ptr : connection identifier.

    void *win_ptr : window identifier.

  - return

    반환값이 없다.

- mlx_destroy_window

  - description

    윈도우를 삭제하는 함수이다.

  - synopsys

    ```c
    int mlx_destory_window(void *mlx_ptr, void *win_ptr);
    ```

  - parameter

    void *mlx_ptr : connection identifier.

    void *win_ptr : window identifier.

  - return

    반환값이 없다.