# save_to_bmp

---

cub3d 실행 시, --save 라는 플래그가 들어갈 경우 요구하는 기능이 있다.

처음 실행된 화면을 bmp 파일로 저장하는 것이다.

크게 어려운 기능은 아니었지만, bmp에 대한 학습이 필요했다.

--save가 올 경우, bmp 헤더에 특정 값들을 대입하고, padding을 고려하여 윈도우의 데이터를 bmp의 데이터에 대입해주면 된다.

헤더는 아래를 참조바란다.

![BMP_header](https://github.com/HyeonsikBae/42Seoul/blob/master/cud3d/BMP_header.png)