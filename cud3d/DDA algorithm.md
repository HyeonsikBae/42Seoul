# DDA algorithm

---

DDA란 Digital Differential Analyzer 를 뜻한다.

2차원의 평면좌표계에서 기울어진 직선을 긋는 방법 중 하나이다.

아래의 2차원 함수로 예를 들어보자.

```
y = 1/3 x + 1
```

이 함수를 평면좌표계에 직선과 디지털로 나타내면 아래와 같다.

![DDA_example](https://github.com/HyeonsikBae/42Seoul/blob/master/cud3d/DDA_example.png)

이렇게 직선을 이루는 좌표값들을 디지털화한 근사값으로 직선처럼 보이게끔 나타내는 것이 DDA 알고리즘이다.

실수값을 정수값으로 변환하는 연산이 많아 느린 것이 단점으로, 이 단점을 극복한 방법은 Bresenham's Algorithm이 있다.

알고리즘의 구현 단계에 대해서는 아래 코드와 함께 설명하겠다.

- Parameter

  ```c
  void	dda(double x_init, double y_init, double x_last, double y_last)
  ```

  dda 알고리즘의 인자로는 아래와 같은 값이 들어간다.

  1. 직선의 시작 좌표 (x_init, y_init)
  2. 직선의 마지막 좌표 (x_last, y_last)



- calculate difference

  ```c
  double	x_delta = x_last - x_init;
  double	y_delta = y_last - y_init;
  ```

  시작 좌표와 마지막 좌표 사이의 x 변화량 및 y 변화량을 구한다.



- calculate slope

  ```c
  double	slope = y_delta / x_delta;
  ```

  직선의 기울기를 구한다.



- set guide

  ```c
  int		step;
  
  if (x_delta >= y_delta)
  	step = abs(x_delta);
  else
  	step = abs(y_delta);
  ```

  x의 변화량과 y의 변화량 중 큰 값의 절대값을 기준으로 삼는다.

  기준에 따라 어느 축을 기준으로 dda 알고리즘이 동작할지 정해진다.



- calculate increase

  ```c
  double	x_inc, y_inc;
  
  // x축 기준
  if (x_delta >= y_delta)
  {
  	y_inc = y_delta / step;
  	if (x_delta >= 0)
  		x_inc = 1;
  	else
  		x_inc = -1;
  }
  // y축 기준
  else
  {
  	x_inc = x_delta / step;
  	if (y_delta >= 0)
  		y_inc = 1;
  	else
  		y_inc = -1;
  }
  ```

  앞서 구한 기준에 따라 x값과 y값의 증가량을 구한다.



- dda 및 결과 출력

  ```c
  int		i = 0;
  
  while (i <= step)
  {
      if (abs(x_inc) == 1)
          printf("x : %f\ty : %f\n", x_init, round(y_init));
      else
          printf("x : %f\ty : %f\n", round(x_init), y_init);
      x_init += x_inc;
      y_init += y_inc;
      i++;
  }
  ```



- 출력 예제

  - Input

    ```
    시작 좌표 : (2, 7)
    마지막 좌표 : (-9, -25)
    ```

  - output

    ```
    x : 2.000000	y : 7.000000
    x : 1.000000	y : 4.000000
    x : 0.000000	y : 1.000000
    x : -1.000000	y : -2.000000
    x : -2.000000	y : -5.000000
    x : -3.000000	y : -8.000000
    x : -4.000000	y : -10.000000
    x : -5.000000	y : -13.000000
    x : -6.000000	y : -16.000000
    x : -7.000000	y : -19.000000
    x : -8.000000	y : -22.000000
    x : -9.000000	y : -25.000000
    ```

    

  

  