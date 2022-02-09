--first clone to your device
+ git clone https://github.com/youzitsu/lempstack_docker.git

-- access lempstack_docker the new folder clone about

-- run dockerfile ---> new image
+ docker build -t php:version1 -f dockerfile ./config_php
+ docekr build -t nginx:version1 -f dockerfile ./config_nginx
+ docker build -t mysql:version1 -f dockerfile ./config_mysql

-- create network
+ docker network create --driver bridge lemp

-- create container from image php:version1,nginx:version1,mysql:version1

+ docker run -d --network lemp --name php -h php -p 9000:9000 php:version1
+ docker run -d --network lemp --name webserver -h nginx -p 80:80 -p 443:443 nginx:version1
+ docker run -d --network lemp --name mysql -h mysql -e MYSQL_ROOT_PASSWORD=kuuhaku -p 3333:3306 mysql:version1


--- access container msyql create database, user...

+ docker exec -it mysql mysql -uroot -pkuuhaku
+ CREATE USER 'luuphuong'@'%' IDENTIFIED BY 'kuuhaku';
+ create database sinhvien;
+ GRANT ALL PRIVILEGES ON sinhvien.* TO 'luuphuong'@'%';
+ flush privileges;
+ show databases;
+ exit;


-- connect container mysql with mysql workbench
+ input ip device, port:3333  , username: luuphuong, passwork: kuuhaku


--open browser:  localhost
