版本 3.4，3.5

标签： &lt;input&gt; ，也可以用SpringMVC的&lt;form:input&gt;。不要用&lt;select&gt;标签。

数据格式： \[{id: "inputvalue1_",text: "_input\_text1"}, {id: "inputvalue2_",text: "_input\_text2"}\]，使用mybatis生成map数组会把属性名大写，要注意转换成小写



使用ajax远程获取数据

```javascript
$("#"+id).select2({
    placeholder: "",
    ajax: { 
        url: "url", 
        dataType: 'json',
        data: function (term, page) {
            return {d: param};
        },
        results: function (data, page) {
            var dt = [];
            for(var i=0;i<data.length;i++ ){
                var dd = {id: data[i]["ID"],text: data[i]["TEXT"]}
                dt.push(dd);
            }
            return {results: dt};
        }
    } ,
    initSelection: function(element, callback) {
        var id = $(element).val();
        if (id !== "") {
            $.ajax("${ctx}/allocation/assignmentRuleConfig/initdc?type=assignmentD&value=" + id, {
                dataType: "json"
            }).done(function(data) { 
	                var dd = {id: data[0]["ID"],text: data[0]["TEXT"]};
                callback(dd); 
            });
        }
    }
});
```



