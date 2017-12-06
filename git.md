# Git

git是分布式版本管理系统。与之相对应的是集中版本管理系统。集中版本管理系统有svn。

使用工具：TortoiesGit，svn的有TortoiesSvn。

重要的命令：

* git init --bare （创建一个空仓库）

* git clone

* git remote

* git fetch

* git pull

* git push

## git clone



```
$ git clone <版本库的网址> <本地目录名>
```

```
$ git clone http[s]://example.com/path/to/repo.git/
$ git clone ssh://example.com/path/to/repo.git/
$ git clone git://example.com/path/to/repo.git/
$ git clone /opt/git/project.git 
$ git clone file:///opt/git/project.git
$ git clone ftp[s]://example.com/path/to/repo.git/
$ git clone rsync://example.com/path/to/repo.git/
```

ssh协议的另一种写法

```
$ git clone [user@]example.com:path/to/repo.git/
```



