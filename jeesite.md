# SpringMVC标签

## &lt;form:form&gt;标签

&lt;form:form id="searchForm" modelAttribute="queryAPSDetailDTO" action="\#" method="post" class="breadcrumb form-search"&gt;

## &lt;form:select&gt;标签

JSP代码：

```
<form:select path="corpname" class="input-xlarge" >
    <form:option value="" label="" />
    <form:options items="${fns:getBranchOfficeGrade('')}" itemLabel="name" itemValue="id" htmlEscape="false" />
</form:select>
```

Java代码：

```
public static List<Office> getBranchOfficeGrade(String grade){
    List<Office> officeList = (List<Office>)CacheUtils.get(CAHCHE_OFFICE_GRADE_LIST+"_"+grade);
    if (officeList == null){
        Office office = new Office();
        office.setGrade(grade);
        officeList = officeDao.findBranchOfficeGrade(office);
        CacheUtils.put(CAHCHE_OFFICE_GRADE_LIST+"_"+grade, officeList);
    }
    return officeList;
}
```

fns函数见另外笔记

items是一个Office的List，itemLabel是office的一个属性name,itemValue对应office的另一个属性id；

itemLabel是下拉框option的text属性，itemValue是option的value属性

## &lt;form:input&gt;标签

`<form:input path="applyNo" htmlEscape="false" maxlength="80" class="input-xlarge"/>`

form标签的path属性值是&lt;form:form&gt;标签的modelAttribute对象的属性；

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



