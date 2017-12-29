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
```

删除容器

```
sudo docker rm mysql
```



