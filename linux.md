# Linux

1、修改目录及其子目录和文件的权限

```
chmod -R 777 dirname
```

## Docker

```
sudo apt-get install docker-io
```

## Mysql

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

$ docker run -d -e MYSQL_ROOT_PASSWORD=admin --name mysql -v /data:/var/lib/mysql -p 3306:3306 mysql
```

删除容器

```
sudo docker rm mysql
```



