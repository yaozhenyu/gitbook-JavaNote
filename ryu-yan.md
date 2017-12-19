# R语言

安装

```
sudo apt-get install r-base-core
```

# Rserve

```
进入R命令行:
install.packages("Rserve")
启动
R CMD INSTALL Rserve_1.8-5.tar.gz
需要远程连接需要输入
R CMD Rserve --RS-enable-remote
```

## Java中使用Rserve

依赖:REngine.jar, RserveEngine.jar

```
RConnection c;
try {
	c = new RConnection();
	REXP x = c.eval("R.version.string");
	System.out.println(x.asString());
	System.out.println("connected!");
	c.eval("setwd('f:/R_Stat/')");
	c.eval("dev.off()");
	c.close();
}catch (Exception e) {
	System.out.println("Error");
		e.printStackTrace();
	} finally {
		System.out.println("finally");
	}
}
```



