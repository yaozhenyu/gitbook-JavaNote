# JSP常用标签

jstl标签需要引入

```
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

## &lt;fmt:formatNumber&gt;标签

&lt;fmt:formatNumber&gt;标签用于格式化数字，百分比，货币。

```
<fmt:formatNumber type="number" pattern="###.#">108.75</fmt:formatNumber> 四舍五入
<fmt:formatNumber type="number" pattern="#.####E0">9557</fmt:formatNumber> 科学计数法
<fmt:formatNumber type="percent">0.98</fmt:formatNumber> 百分比
<fmt:formatNumber value="12" type="currency" pattern="$.00"/> $12.00  
<fmt:formatNumber value="12" type="currency" pattern="$.0#"/> $12.0   
<fmt:formatNumber value="1234567890" type="currency"/> $1,234,567,890.00(那个货币的符号和当前web服务器的 local 设定有关)   
<fmt:formatNumber value="123456.7891" pattern="#,#00.0#"/> 123,456.79   
<fmt:formatNumber value="123456.7" pattern="#,#00.0#"/>  123,456.7   
<fmt:formatNumber value="123456.7" pattern="#,#00.00#"/> 23,456.70   
<fmt:formatNumber value="12" type="percent" /> 1,200% (type 可以是currency、 number、 和percent)。
<fmt:formatNumber value="123999999999" pattern="#0.##"/> 不使用科学计数法
```

## &lt;fmt:formatDate&gt;标签

&lt;fmt:formatDate&gt;标签用于格式化日期。

```
<fmt:formatDate value="${actCreditApplyProcess.beginDate}" pattern="yyyy-MM-dd"/> 年月日
pattern="yyyy-MM-dd HH:mm:ss"(h大写位24小时表示法,小写的为12小时表示法) 年月日时分秒
```



