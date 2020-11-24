# Project procedure

ft_server의 Mendatory 만족을 위한 순차적 기능 구현

---

1. debian buster

   과제가 요구한 container 의 OS가 debian buster이기 때문에 도커 공식 이미지 저장소에서 debian:buster의 이미지를 내려받는다.

   ```shell
   $> docker pull debian:buster
   ```

   debian:buster의 이미지를 내려받고 나면 아래와 같은 명령을 통해 내려받는 이미지들의 목록을 확인할 수 있다.

   ```shell
   $> docker images
   REPOSITORY			TAG			COMMAND			CREATED			SIZE
   debian				buster		ef05c61d5112	2 days ago		114MB
   ```

   과제가 요구한 in only one docker container조건을 만족시키기 위해서 docker를 실행하고 내부에서 다음 요구사항들을 해결하도록 한다.

   ```shell
   $> docker run -it debian:buster
   ```

   debian을 실행시키면서 2개의 옵션을 넣었다.

   -i : interactive. 컨테이너와 상호작용을 위한 옵션

   -t : tty 사용. 터미널과 비슷한 환경 조성.

   

   **도커를 실행시킨 뒤로 쉘에 명령어 입력창이 root@ef05c61d5112:/# 과 같은 형식으로 변했을 것이다. 하지만 과제 정리를 위해서는 커맨드 입력창을 $>로 사용할 것이다**

   

2. Nginx

   Nginx 설치 전에 package manager를 업데이트 하도록 하자.

   ```shell
   $> apt update -y
   ```

   package manager 업데이트를 통해 설치 가능한 프로그램들의 version이 변경될 것이다.

   y 옵션을 통해 동의를 구하지 않고 명령어가 실행되도록 할 것이며, 앞으로도 계속 넣어줄 것이다.

   이제 아래 명령어를 통해 Nginx를 설치해보자
   
   ```shell
   $> apt install -y nginx
   ```
   
   nginx가 정상적으로 설치되었다면 version 확인을 통해 설치가 잘 되었는지 확인할 수 있다.
   
   ```shell
   $> nginx -v
   nginx version: nginx/1.14.2
   ```
   
   nginx가 설치 되었다면 컨테이너 내부에서 실행될 nginx와 로컬 간 포트를 설정해주어야 한다.
   
   컨테이너를 종료하자.
   
   ```shell
   $> exit
   ```
   
   실행된 컨테이너 ID를 확인 후,
   
   ```shell
   $> docker ps -a
   CONTAINER ID IMAGE           COMMAND     CREATED         STATUS                  PORTS       NAMES
   dbecea8936d2 debian:buster   "bash"      31 hours ago    Exited 19 seconds ago               hyeonsik
   ```
   
   nginx까지 설치된 컨테이너를 이미지로 만들기 위해 docker commit을 실행하자.
   
   ```shell
   $> docker commit dbecea8936d2 project:ft_server
   ```
   
   80번 포트를 개방하고 컨테이너를 다시 실행하자.
   
   ```shell
   $> docker run -it -p 80:80 project:ft_server
   ```
   
   nginx를 실행하고, 상태를 확인해보자.
   
   ```shell
   $> service --status-all
    [ ? ]  hwclock.sh
    [ - ]  nginx
   $> service nginx status
   [FAIL] nginx is not running ... failed!
   $> service nginx start
   [ ok ] Starting nginx: nginx.
   $> service nginx status
   [ ok ] nginx is running.
   $> service --status-all
    [ ? ]  hwclock.sh
    [ + ]  nginx
   ```
   
   http://127.0.0.1 에 접속하여 nginx의 실행 여부를 확인할 수 있다.

   

3. PHP

   php와 nginx, wordpress, MySQL 등을 연동하기 위한 PFP-FPM 설치를 하자.

   ```shell
   $> apt install -y php-fpm
   ```

   -v 옵션을 통해 정상적인 설치 여부를 확인하자.

   ```shell
   $> php -v
   ```

   php와 nginx 연동을 위해 nginx.conf 파일 변경이 필요하다.

   파일 변경을 위해 vim을 설치하도록 하자.

   ```shell
   $> apt install -y vim
   ```

   /etc/nginx/sites-enabled/default 파일을 변경하자.

   1. Fast CGI 설정 변경

   ```shell
   # 변경 전
   # pass PHP scripts to FastCGI server
   #
   #location ~ \.php$ {
   #       include snippets/fastcgi-php.conf;
   #
   #       # With php-fpm (or other unix sockets):
   #       fastcgi_pass unix:/run/php/php7.3-fpm.sock;
   #       # With php-cgi (or other tcp sockets):
   #       fastcgi_pass 127.0.0.1:9000;
   #}
   
   # 변경 후
   # pass PHP scripts to FastCGI server
   #
   location ~ \.php$ {
          include snippets/fastcgi-php.conf;
   #
   #       # With php-fpm (or other unix sockets):
          fastcgi_pass unix:/run/php/php7.3-fpm.sock;
   #       # With php-cgi (or other tcp sockets):
   #       fastcgi_pass 127.0.0.1:9000;
   }
   ```

   2. index.php 추가

   ```shell
   # 변경 전
   index index.html index.htm index.nginx-debian.html;
   # 변경 후
   index index.html index.htm index.nginx-debian.html index.php;
   ```

   3. autoindex on 추가

   ```shell
   autoindex on;
   ```

   php를 실행, nginx를 재실행한다.

   ```shell
   $> service php7.3fpm start
   $> service nginx restart
   $> service --status-all
    [ ? ]  hwclock.sh
    [ + ]  nginx
    [ + ]  php7.3-fpm
    [ - ]  procps
   ```

   php 연동을 확인하기 위해 phpinfo.php 파일을 /var/www/html 디렉토리 내에 저장한다.

   코드는 아래와 같다.

   ```php
   <?php
   phpinfo();
   ?>
   ```

   이제 http://127.0.0.1/phpinfo.php 에 접속하여 php가 정상적으로 동작되는지 확인할 수 있다.

4. MySQL

   database 사용을 위해 mariaDB를 설치하도록 하자

   ```shell
   $> apt install -y mariadb-server
   ```

   DB 서버에 접근하기 위해 DB 서버를 구동하도록 하자.

   ```shell
   $> service mysql start
   ```

   이제 database에 접근하기 위해 DB 서버에 접속하여 user를 생성하도록 하자.

   ```shell
   $> mysql
   
   MariaDB [(none)]> create user 'hybae'@'localhost' identified by 'password';
   Query OK, 0 rows affected (0.000 sec)
   MariaDB [(none)]> grant all privileges on *.* to hybae@'localhost';
   Query OK, 0 rows affected (0.000 sec)
   MariaDB [(none)]> flush privileges;
   Query OK, 0 rows affected (0.000 sec)
   MariaDB [(none)]> exit
   Bye
   ```

   MySQL 설치가 끝났지만, PHP와의 연동이 남았다.

   연동을 위해 PHP-MySQL 연동 모듈을 설치하도록 하자.

   ```shell
   $> apt install -y php-mysql
   ```

   MySQL용 무료 오픈 소스 관리 도구인 phpMyAdmin을 설치하도록 하자.

   해당 도구는 패키지로 받지 않고 직접 파일을 내려받는다.

   wget 명령어를 이용해야 하므로 wget 명령어를 다운받는다.

   ```shell
   $> apt install -y wget
   ```

   wget을 통해 phpMyAdmin을 다운받고 압축을 해제한다.

   ```shell
   $> wget -O /var/www/html/phpmy.tar.gz https://files.phpmyadmin.net/phpMyAdmin/4.9.7/phpMyAdmin-4.9.7-all-languages.tar.gz
   $> tar -zxvf /var/www/html/phpmy.tar.gz -C /var/www/html
   ```

   php-7.3fpm을 재시작하여 phpMyAdmin을 적용시킨다.

   ```shell
   $> service php7.3-fpm restart
   ```

   http://127.0.0.1/phpMyAdmin-4.9.7-all-languages/index.php 에 접속하여 MySQL에서 생성한 계정으로 접속하여 연동이 성공적으로 이루어졌음을 확인할 수 있다.

   하지만 여기서 세 가지 에러를 확인할 수 있다.

   - mbstring PHP extension 을 찾을 수 없거나 multibyte charset 을 사용한 것 같습니다. mbstring PHP extension 이 없다면 phpMyAdmin 에서 문자열을 정확하게 나눌 수 없으며 이로 인해 예상하지 못한 결과가 발생 할 수 있습니다.
   - 이제 설정 파일은 암호화 문자열(blowfish_secret)을 필요로 합니다.
   - $cfg[]TempDir''(./tmp/)에 액세스할 수 없음. phpMyAdmin은 템플릿을 캐시할 수 없으며 이로 인해 속도가 느려질 것이다.

   아래에서 이 에러들의 해결방법에 대해 기술하겠다.

   첫 번째 에러는 non-ASCII 문자열을 처리하지 못하는 것으로, 확장모듈 설치 후 php를 재시작하여 해결할 수 있다.

   ```shell
   $> apt install -y php-mbstring
   $> service php7.3-fpm restart
   ```

   두 번째 에러는 blowfish_secret 이라는 고유 랜덤 키를 입력해주면 된다.

   /var/www/html/phpMyAdmin-4.9.7-all-languages/config.inc.php 의 $cfg['blowfish_secret'] 에 임의의 46바이트 값을 넣어주면 해결된다.

   세 번재 에러는 웹 서버를 구동하는 계정이 phpMyAdmin에 접근이 불가능해 발생하는 오류이다.

   ps 명령어를 사용하면 웹 서버 데몬의 UID를 확인할 수 있다.

   ```shell
   $> ps -ef
   UID        PID  PPID  C STIME TTY          TIME CMD
   root         1     0  0 Nov19 pts/0    00:00:00 bash
   root        55     1  0 Nov19 ?        00:00:00 nginx: master process /usr/sbin/nginx
   www-data    56    55  0 Nov19 ?        00:00:00 nginx: worker process
   www-data    57    55  0 Nov19 ?        00:00:00 nginx: worker process
   www-data    59    55  0 Nov19 ?        00:00:00 nginx: worker process
   www-data    60    55  0 Nov19 ?        00:00:00 nginx: worker process
   www-data    61    55  0 Nov19 ?        00:00:00 nginx: worker process
   www-data    62    55  0 Nov19 ?        00:00:00 nginx: worker process
   www-data    64    55  0 Nov19 ?        00:00:00 nginx: worker process
   www-data    65    55  0 Nov19 ?        00:00:00 nginx: worker process
   ```

   웹 서버 데몬의 UID는 www-data인 것을 알 수 있다.

   ls 명령어를 통해 /var/www/html 경로의 소유자를 확인해보자

   ```shell
   $> ls -l /var/www/html/
   -rw-r--r--  1 root root      612 Nov 19 05:39 index.nginx-debian.html
   drwxr-xr-x 12 root root     4096 Nov 20 03:10 phpMyAdmin-4.9.7-all-languages
   -rw-r--r--  1 root root       20 Nov 19 06:15 phpinfo.php
   -rw-r--r--  1 root root 10190261 Oct 15 18:50 phpmy.tar.gz
   ```

   phpMyAdmin의 소유자는 root임을 알 수 있다.

   데몬의 주체와 phpMyAdmin 파일 소유자를 맞춰주기 위해 /var/www/html/ 경로 소유자를 www-data로 변경시켜주자

   ```shell
   $> chown -R www-data /var/www/html/
   ```

   다시 한 번 phpMyAdmin에 접속하면 모든 에러가 사라지는 걸 확인할 수 있다.

   

5. WordPress

   WordPress를 사용하기 위해 db가 필요하다.

   기존의 db를 사용해도 좋지만 wordpress용 db를 새로 생성한다.

   ```shell
   $> mysql
   MariaDB [(none)]> create user wp_hybae@'localhost' identified by 'password';
   MariaDB [(none)]> create database wp_db default CHARACTER SET UTF8;
   MariaDB [(none)]> grant all privileges on wp_db.* to wp_hybae@'localhost';
   MariaDB [(none)]> flush privileges;
   ```

   wordpress 또한 phpMyAdmin과 같이 서버에서 파일을 내려받는다.

   ```shell
   $> wget -O /var/www/html/wordpress.tar.gz https://wordpress.org/latest.tar.gz
   $> tar -zxvf /var/www/html/wordpress.tar.gz -C /var/www/html
   ```

   wordpress 사용을 위해 /var/www/html/wordpress 경로의 wp-config.php 파일을 아래와 같이 수정한다.

   DB_NAME, DB_USER, DB_PASSWORD 값 삽입.

   http://127.0.0.1/wordpress/wp-admin/install.php 에 접속하여 설치과정을 마치고 나면 wordpress가 실행된다.

   

6. SSL/TLS 적용

   개인키를 생성한다.

   ```shell
   $> openssl genrsa -out priv.key 2048
   ```

   CSR을 생성한다.

   ```shell
   $> openssl req -new -key priv.key -out req.csr
   ```

   CSR을 인증 기관에 전송하여 인증서를 발급받는다.

   ```shell
   $> openssl genrsa -out MyrootCA.key 2048
   $> openssl req -x509 -new -subj "/C=KR/ST=Gyeonggi/L=Suwon/O=42S/OU=Seoul/CN=hybae" -nodes -key MyrootCA.key -days 365 -out MyrootCA.pem
   $> openssl x509 -req -in req.csr -CA /MyrootCA.pem -CAkey MyrootCA.key -CAcreateserial -out gen.crt -days 365
   ```

   /etc/nginx/sites-enabled/default 에 개인키와 인증서 그리고 TLS 버전을 적용한다.

   ```shell
   server {
   	listen 443 ssl;		# 변경
   
   	ssl_certificate			/gen.crt;		# 추가
   	ssl_certificate_key		/priv.key;		# 추가
   	ssl_protocols			TLSv1.2 TLSv1.3;# 추가
   }
   ```

7. 리다이렉트

   리다이렉트를 위해선 두 가지가 필요하다.

   첫째로 default에 소스 추가

   ```shell
   server {
   	listen 80 default_server;
   	server_name _;
   	return 301 https://$host$request_uri;
   }
   ```

   두번째로 도커 실행 시, 443 포트를 여는 것.

   ```shell
   $> docker run -it -p 80:80 -p 443:443 [REPO:TAG]
   ```
