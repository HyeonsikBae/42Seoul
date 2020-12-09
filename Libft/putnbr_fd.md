## putnbr_fd

- 매개변수로 들어오는 파일 디스크립터에 매개변수로 들어오는 정수를 출력하는 함수

- SYNOPSIS

  ```c
  void	putnbr_fd(int n, int fd)
  ```

- CODE

  ```c
  {
  	char    temp;
  
  	if (n < 0)
  	{
  		temp = '-';
  		write(fd, &temp, 1);
  		if (n == -2147483648)
  		{
  			temp = '2';
  			write(fd, &temp, 1);
  			n = -147483648;
  		}
  		n = -n;
  	}
  	if (n >= 10)
  		ft_putnbr_fd(n / 10, fd);
  	temp = n % 10 + '0';
  	write(fd, &temp, 1);
  }
  ```
  
- 동작

  1. n 이 음수인 경우, - 출력

     1-1. n 이 음의 정수 최소값인 경우 2 출력

     1-2. n 에 -1 곱함.

  2. n 이 10 이상인 경우, n / 10을 매개변수로 하여 함수 재귀

  3. n 을 10으로 나눈 나머지 출력