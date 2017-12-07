## Docker

```
sudo apt-get install docker-io
```

启动一个容器

```
docker run --name first-mysql -p 3306:3306 -e MYSQL\_ROOT\_PASSWORD=123456 -d mysql
```

启动一个停止的容器

```
sudo docker start container_id
```

重新启动一个容器

```
sudo docker restart container_id
```

删除容器

```
sudo docker rm -f mysql
```

进入一个正在运行的容器

```
docker exec -it 容器名 /bin/sh 或者 docker exec -it 容器id /bin/sh
```

**安装Oracle数据库**

```
sudo docker search oracle
sudo docker pull sath89/oracle-12c
sudo docker run -d -p 8080:8080 -p 1521:1521 -v ~/oracle/data:/u01/app/oracle sath89/oracle-12c

docker ps
docker exec -it 9e893d773494 /bin/bash
netstat -nlpt      // 启动数据库服务（重要）
su oracle
$ORACLE_HOME/bin/sqlplus / as sysdba   // 登际sqlplus

alter user system identified by oracle; // 修改密码

// 安装好的数据库初始状态
hostname: localhost
port: 1521
sid: xe
username: system
password: oracle
```

**安装Mysql数据库**

```
sudo docker pull mysql
```

运行一个mysql容器

```
sudo docker run --name first-mysql -p 3306:3306 -e MYSQL\_ROOT\_PASSWORD=123456 -d mysql


// 命令解释
run            运行一个容器
--name         后面是这个镜像的名称
-p 3306:3306   表示在这个容器中使用3306端口(第二个)映射到本机的端口号也为3306(第一个)
-d


// 本机目录挂载到docker容器 加 -v 参数
$ docker run -d -e MYSQL_ROOT_PASSWORD=admin --name second-mysql -v ~/mysql/data:/var/lib/mysql -p 3307:3306 mysql
```



