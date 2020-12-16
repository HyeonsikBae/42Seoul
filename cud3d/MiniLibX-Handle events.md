# MiniLibX - Handle events

---

MiniLibX 의 Handle events 파트엔 5가지의 함수가 구현되어 있다.

그래픽 시스템은 키보드와 마우스 등으로 정보를 얻고, 픽셀 이미지 등을 표시하기 위해 화면에 명령을 보낸다. 이를 위해 프로그램은 키보드나 마우스에서 이벤트를 수신한다.

### mlx_loop

- description

  무한루프에서 유저가 정의한 특정 이벤트를 기다리게 하는 함수

  - 키보드 입력, 마우스 입력, expose

- synopsys

  ```c
  int mlx_loop(boid *mlx_ptr);
  ```

- parameter

  void *mlx_ptr : connection identifier




### mlx_key_hook

- description

  키 입력에 대한 이벤트 핸들러

- synopsys

  ```c
  int mlx_key_hook(void *win_ptr, int (*funct_ptr)(), void *param);
  ```

- parameter

  vold *win_ptr : window identifier

  int (*funct_ptr)() : 원하는 기능의 함수 포인터

  void *param : 함수로 넘겨줄 변수



### mlx_mouse_hook

- description

  마우스 입력에 대한 이벤트 핸들러

- synopsys

  ```c
  int mlx_mouse_hook(void *win_ptr, int (*funct_ptr)(), void *param);
  ```

- parameter

  vold *win_ptr : window identifier

  int (*funct_ptr)() : 원하는 기능의 함수 포인터

  void *param : 함수로 넘겨줄 변수



### mlx_expose_hook

- description

  expose에 대한 이벤트 핸들러

  expose 란 창의 일부를 다시 그리는 이벤트를 말한다.

- synopsys

  ```c
  int mlx_expose_hook(void *win_ptr, int (*funct_ptr)(), void *param);
  ```

- parameter

  vold *win_ptr : window identifier

  int (*funct_ptr)() : 원하는 기능의 함수 포인터

  void *param : 함수로 넘겨줄 변수



### mlx_loop_hook

- description

  이벤트가 발생되지 않는 경우의 핸들러

- synopsys

  ```c
  int mlx_loop_hook(void *win_ptr, int (*funct_ptr)(), void *param);
  ```

- parameter

  vold *win_ptr : window identifier

  int (*funct_ptr)() : 원하는 기능의 함수 포인터

  void *param : 함수로 넘겨줄 변수



### 호출되는 함수

MiniLibX에 의해 이벤트를 확인했을 경우, MiniLibX는 아래와 같은 해당 함수들을 호출한다.

- key_hook(void *param);
- mouse_hook(int keycode, void *param);
- expose_hook(void *param);
- loop_hook(void *param);