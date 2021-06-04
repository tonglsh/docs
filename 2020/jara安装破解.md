# jara安装破解

### 数据库安装

docker-compose.yaml

```
version: '3'
services:
  mysql:
    image: mysql/mysql-server:5.7
    container_name: yanfa_mysql_5.7_3888
    restart: always
    ports:
      - "3888:3306"
    volumes:
      - ./my.cnf:/etc/my.cnf
      - ./db_data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: 123456
      MYSQL_ROOT_HOST: "%"
```

对数据配置有要求

https://confluence.atlassian.com/adminjiraserver085/connecting-jira-applications-to-mysql-5-7-981154582.html

my.cnf

```
# For advice on how to change settings please see
# http://dev.mysql.com/doc/refman/5.7/en/server-configuration-defaults.html

[mysqld]
#
# Remove leading # and set to the amount of RAM for the most important data
# cache in MySQL. Start at 70% of total RAM for dedicated server, else 10%.
# innodb_buffer_pool_size = 128M
#
# Remove leading # to turn on a very important data integrity option: logging
# changes to the binary log between backups.
# log_bin
#
# Remove leading # to set options mainly useful for reporting servers.
# The server defaults are faster for transactions and fast SELECTs.
# Adjust sizes as needed, experiment to find the optimal values.
# join_buffer_size = 128M
# sort_buffer_size = 2M
# read_rnd_buffer_size = 2M
skip-host-cache
skip-name-resolve
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock
secure-file-priv=/var/lib/mysql-files
user=mysql

default-storage-engine=INNODB
character_set_server=utf8mb4
innodb_default_row_format=DYNAMIC
innodb_large_prefix=ON
innodb_file_format=Barracuda
innodb_log_file_size=2G
sql_mode = NO_AUTO_VALUE_ON_ZERO

# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0

log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

```

在准备好的MySQL中创建数据库

```
CREATE DATABASE jiradb CHARACTER SET utf8mb4 COLLATE utf8mb4_bin; 
```

执行以下命令(自行替换ip 端口等)

```none
GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER,INDEX on jiradb.* TO 'root'@'192.168.50.66' IDENTIFIED BY '123456';
flush privileges;
```

### 安装jira

jira使用的是8.5.1版本，docker-compose: 

```
version: '2' 
services: 
  jira: 
    image: atlassian/jira-software:8.5.1 
    container_name: jira 
    restart: always 
    ports: 
      - "8080:8080" 
    volumes: 
      - ./data:/var/atlassian/jira 
      - ./mysql-connector-java-5.1.49.jar:/opt/atlassian/jira/atlassian-jira/WEB-INF/lib/mysql-connector-java-5.1.49.jar 
      - ./atlassian-extras-3.2.jar:/opt/atlassian/jira/atlassian-jira/WEB-INF/lib/atlassian-extras-3.2.jar 
 
```

下载数据库驱动及破解包

```
wget https://repo1.maven.org/maven2/mysql/mysql-connector-java/5.1.49/mysql-connector-java-5.1.49.jar
```

把atlassian-extras-3.2.jar粘贴到当前路径