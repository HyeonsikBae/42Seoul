# Dockerfile fot fr_server

---

Project Procedure에 따른 절차들을 Dockerfile에 커맨드로 정리하였다.

Docker는 이 Dockerfile을 읽어서 이미지를 빌드한다.

미리 다운 및 수정한 파일은 Dockerfile와 같은 디렉토리 내 srcs라는 폴더 내부에 저장해서 사용하였다.

```dockerfile
FROM debian:buster

COPY srcs/* /tmp/init

RUN apt-get update -y
RUN apt install -y nginx php-fpm php-mysql php-mbstring mariadb-server 
RUN tar -zxvg /var/www/html/phpMyAdmin.tar.gz -C /var/www/html
&& tar -zxvf /var/www/html/wordpress.tar.gz -C /var/www/html
RUN cp /tmp/init/config.inc.php /var/www/hteml/phpMyAdmin/
&& cp /tmp/init/wp-config.php /var/www/html/wordpress/
&& cp /tmp/init/priv.key /
&& cp /tmp/init/gen.crt /
&& rm /etc/nginx/sites-enabled/default
&& cp /tmp/init/default /etc/nginx/sites-enabled/
RUN chown -R www-data /var/www/html
RUN mkdir /var/www/html/test
&& touch /var/www/html/test/sample1
&& touch /var/www/html/test/sample2
RUN service mysql start
&& cat /tmp/init/set.sql | mysql -u root

ENTRYPOINT service php7.3-fpm start && service nginx start && service mysql start &&sleep inf
```

