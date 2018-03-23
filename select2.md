版本 3.4，3.5

**标签：** &lt;input&gt; ，也可以用SpringMVC的&lt;form:input&gt;。不要用&lt;select&gt;标签。

**数据格式：** \[{id: "inputvalue1_",text: "\_input\_text1"}, {id: "inputvalue2_",text: "\_input\_text2"}\]，使用mybatis生成map数组会把属性名大写，要注意转换成小写

使用ajax远程获取数据：

```javascript
$("#selector").select2({
    placeholder: "请选择",
    ajax: { 
        url: "url", 
        dataType: 'json',
        data: function (term, page) {
            return {d: param}; // 请求参数
        },
        results: function (data, page) { // 请求成功数据处理 要用results属性
            var dt = [];
            for(var i=0;i<data.length;i++ ){
                var dd = {id: data[i]["ID"],text: data[i]["TEXT"]}
                dt.push(dd);
            }
            return {results: dt};
        }
    } ,
    initSelection: function(element, callback) { // 初始化数值 如果想要使用select2('val','')方法修改值。该方法必须实现。
        var id = $(element).val();
        if (id !== "") {
            $.ajax("${ctx}/allocation/assignmentRuleConfig/initdc?type=assignmentD&value=" + id, {
                dataType: "json"
            }).done(function(data) { 
                    var dd = {id: data[0]["ID"],text: data[0]["TEXT"]};// 单选
                callback(dd); 
            });
        }
    }
});
```



