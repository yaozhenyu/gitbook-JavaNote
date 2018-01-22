启动一个容器

```
docker run --name first-mysql -p 3306:3306 -e MYSQL\_ROOT\_PASSWORD=123456 -d mysql
```

启动一个停止的容器

```
sudo docker start container_id
```

Oracle数据库

```
sudo docker pull sath89/oracle-12c
sudo docker run -d -p 8080:8080 -p 1521:1521 -v /my/oracle/data:/u01/app/oracle sath89/oracle-12c
```



