# R语言

安装

```
sudo apt-get install r-base-core
```

# Rserve

```
进入R命令行:
R
install.packages("Rserve")
R CMD INSTALL Rserve_1.8-5.tar.gz
需要远程连接需要输入
R CMD Rserve --RS-enable-remote
```

## Java中使用Rserve

依赖:REngine.jar, RserveEngine.jar

```
maven依赖
<!-- https://mvnrepository.com/artifact/org.rosuda.REngine/Rserve -->
<dependency>
    <groupId>org.rosuda.REngine</groupId>
    <artifactId>Rserve</artifactId>
    <version>1.8.1</version>
</dependency>

Java代码

RConnection rcon = new RConnection("114.115.205.210");    //建立远程链接
String rv = rcon.eval("R.version.string").asString();     //得到R版本信息
double[] arr = rcon.eval("rnorm(10)").asDoubles();        //通过R得到10个随机数返回数组
System.out.println(rv);                                   //输出版本信息
for(double x:arr){                                        //遍历集合
    System.out.println(x);
}
```

## RStudio Server

```
$ sudo apt-get install r-base // 安装R语言
$ sudo apt-get install gdebi-core
$ wget https://download2.rstudio.org/rstudio-server-1.1.383-amd64.deb
$ sudo gdebi rstudio-server-1.1.383-amd64.deb
```

访问浏览器`localhosst:8787`

