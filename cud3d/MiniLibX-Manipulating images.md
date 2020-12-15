# MiniLibX - Manipulating images

---

MiniLibX 의 Manipulating images 파트엔 8가지의 함수가 구현되어 있다.

### mlx_new_image

- description

  이미지를 생성하는 함수

- synopsys

  ```c
  void *mlx_new_image(void *mlx_ptr, int width, int heigth);
  ```

- parameter

  void *mlx_ptr : connection identifier

  int width : 생성할 이미지의 너비

  int heigth : 생성할 이미지의 높이

  

### mlx_get_data_addr

- description

  생성된 이미지의 정보를 반환해주는 함수

- synopsys

  ```c
  char *mlx_get_data_addr(void *img_ptr, int *bits_per_pixel, int *size_line, int *endian);
  ```

- parameter

  void *img_ptr : 사용할 이미지의 주소

  int *bits_per_pixel : 픽셀 색상을 표현하는 데 필요한 비트 수

  int *size_line : 이미지 한 줄을 메모리에 저장하는데 사용되는 바이트 수

  int *endian : 0 = little endian, 1 = big endian

  

### mlx_put_image_to_window

- description

  이미지를 윈도우에 올리는 함수

- synopsys

  ```c
  int	mlx_put_image_to_window(void *mlx_ptr, void *win_ptr, void *imt_ptr, int x, int y)
  ```

- parameter

  void *mlx_ptr : connection identifier

  void *win_ptr : window identifier

  void *img_ptr : image identifier

  int x : 윈도우의 x 좌표

  int y : 윈도우의 y 좌표

  

### mlx_get_color_value

- description

  디스플레이에 따라 픽셀 저장에 사용되는 비트 수가 변경될 수 있는데, 이것을 이미지의 bits_per_pixel 에 맞춰 변환하는 함수

  변환이 필요하지 않은 경우, 사용할 필요가 없으며 이미지의 endian이 로컬 endian과 다른 경우 값을 사용하기 전에 변환해야 한다.

- synopsys

  ```c
  unsigned int mlx_get_color_value(void *mlx_ptr, int color);
  ```

- parameter

  void *mlx_ptr : connection identifier

  int color : 특정 컬러

  

### mlx_xpm_to_image

- description

  xpm 데이터로 새로운 이미지를 만드는 함수.

  에러 발생 시 NULL반환.

- synopsys

  ```c
  void *mlx_xpm_to_image(void *mlx_ptr, char **xpm_data, int *width, int *height);
  ```

- parameter

  void *mlx_ptr : connection identifier

  char **xpm_data : xpm data

  int *width : 생성할 이미지의 너비

  int *heigth : 생성할 이미지의 높이

  

### mlx_xpm_file_to_image

- description

  xpm 파일로 새로운 이미지를 만드는 함수

  에러 발생 시 NULL반환.

- synopsys

  ```c
  void *mlx_xpm_file_to_image(void *mlx_ptr, char *filename, int *witdh, int *height);
  ```

- parameter

  void *mlx_ptr : connection identifier

  char *filename : xpm file

  int *width : 생성할 이미지의 너비

  int *height : 생성할 이미지의 높이

  

### mlx_png_file_to_image

- description

  png 파일로 새로운 이미지를 만드는 함수

  에러 발생 시 NULL반환.

- synopsys

  ```c
  void *mlx_png_file_to_image(void *mlx_ptr, char *filename, int *width, int *height);
  ```

- parameter

  void *mlx_ptr : connection identifier

  char *filename : png file

  int *width : 생성할 이미지의 너비

  int *heigth : 생성할 이미지의 높이

  

### mlx_destroy_image

- description

  image를 삭제하는 함수

- synopsys

  ```c
  int	mlx_destroy_image(void *mlx_ptr, void *img_ptr)l
  ```

- parameter

  void *mlx_ptr : connection identifier

  void *img_ptr : image identifier