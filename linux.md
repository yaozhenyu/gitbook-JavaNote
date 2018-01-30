# Linux

1、修改目录及其子目录和文件的权限

```
chmod -R 777 dirname
```

** 怎么删除登陆界面的用户名\(Ubuntu\)**

```
首先跳转到以下目录

cd /var/lib/AccountsService/users/

ls后可以看到你想要隐藏的某个用户文件

然后打开该文件

vim username

进行更改

[User]
XSession=
SystemAccount=false  //将false改为true
```



