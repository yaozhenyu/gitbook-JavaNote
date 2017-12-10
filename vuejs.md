# Vue.js

通过vue-cli生成的项目,\`vue init webpack myproject\`，访问路径为`http://localhost:8080/#/`

这与我们平常的访问路径不一样，感觉有点别扭，怎么改成我们习惯的样子呢？

在index.js文件加上`mode:'history'`：

```
export default new Router({
    mode:'history',
    routes: [
    {
        path: '/',
        name: 'HelloWorld',
        component: HelloWorld
    }
    ]
})
```



