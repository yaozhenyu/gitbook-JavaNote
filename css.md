# CSS

### css选择器

ID选择器：

```
#red {color:red;}
#green {color:green;}
```

类选择器：

```
.center {text-align: center}
```

属性选择器：

```
[title=W3School]{
    border:5px solid blue;
}
```

派生选择器：

```
li strong {
    font-style: italic;
    font-weight: normal;
}
```

元素选择器：

```
html {color:black;}
h1 {color:blue;}
h2 {color:silver;}
```

伪类：

##### 锚伪类

```
a:link {color: #FF0000}        /* 未访问的链接 */
a:visited {color: #00FF00}    /* 已访问的链接 */
a:hover {color: #FF00FF}    /* 鼠标移动到链接上 */
a:active {color: #0000FF}    /* 选定的链接 */
```

##### :first-child 伪类



伪元素：

##### :first-line 伪元素  --  用于向文本的首行设置特殊样式。

```
p:first-line{
  color:#ff0000;
  font-variant:small-caps;
}
```

##### :first-letter --  用于向文本的首字母设置特殊样式

```
p:first-letter{
  color:#ff0000;
  font-size:xx-large;
}
```



