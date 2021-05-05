## docker 方式部署mysql

参考（https://dev.mysql.com/doc/refman/8.0/en/docker-mysql-getting-started.html） 

拉镜像：

```
docker pull mysql/mysql-server:lastest
```

better：

```
docker run --name=mysql-tonglsh -e MYSQL_ROOT_PASSWORD=999gml  -p 3306:3306 
-v /home/tonglsh/Mysqldb/data:/var/lib/mysql 
-v /home/tonglsh/Mysqldb/conf:/etc/mysql 
-v /home/tonglsh/Mysqldb/log:/var/log/mysql 
-v /home/tonglsh/Mysqldb/mysql-files:/var/lib/mysql-files
-d mysql/mysql-server:latest
```

运行容器：

```
docker run --name=mysql-tonglsh --restart on-failure -p 3306:3306 -v /home/tonglsh/myApps/mysqldb:/var/lib/mysql -d mysql/mysql-server:latest
```

查看日志（初始密码）：

```
docker logs mysql-tonglsh
```

进入容器：

```
docker exec -it mysql-tonglsh mysql -uroot -p
```

更换初始密码：

```
ALTER USER 'root'@'localhost' IDENTIFIED BY '999gml';
```

### mysql 访问权限更改（默认只允许localhost）

mysql> use mysql;

mysql> update user set host='%' where user = 'root';
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.01 sec)  