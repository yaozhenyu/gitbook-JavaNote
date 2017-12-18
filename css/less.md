# Less

### 安装：

在服务器端最容易的安装方式就是通过 npm （[node.js](http://nodejs.org/)的包管理器），方法如下：

```
$ npm install -g less
```

### 命令行用法

安装 Less 后，就可以在命令行上调用 Less 编译器了，如下：

```
$ lessc styles.less
```

这将输出编译之后的 CSS 代码到 `stdout`，你可以将输出重定向到一个文件：

```
$ lessc styles.less > styles.css
```

### 变量

举个简单的例子

```
@nice-blue: #5B83AD;
@light-blue: @nice-blue + #111;

#header {
  color: @light-blue;
}
```

编译为：

```
#header
{
  
color
:
#6c94be
;

}
```

注意，由于变量只能定义一次，其本质就是“常量”。

