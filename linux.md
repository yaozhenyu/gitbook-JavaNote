# Linux

1、修改目录及其子目录和文件的权限

```
chmod -R 777 dirname
```

** 怎么删除登陆界面的用户名\(Ubuntu\)**

```
sudo gnome-open /etc/lightdm/lightdm.conf
增加以下两行
greeter-hide-users=true
greeter-allow-guest=false
```



