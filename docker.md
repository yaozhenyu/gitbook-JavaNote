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



