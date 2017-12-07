# SpringMVC标签

## &lt;form:form&gt;标签

&lt;form:form id="searchForm" modelAttribute="dto" action="\#" method="post" class="breadcrumb form-search"&gt;

## &lt;form:select&gt;标签

JSP代码：

```
<form:select path="corpname" class="input-xlarge" >
    <form:option value="" label="" />
    <form:options items="${fns:getBranchOfficeGrade('')}" itemLabel="name" itemValue="id" htmlEscape="false" />
</form:select>
```

Java代码：

public static List&lt;Office&gt; getBranchOfficeGrade\(String grade\){

```java
List<Office> officeList = (List<Office>)CacheUtils.get(CAHCHE_OFFICE_GRADE_LIST+"_"+grade);

if (officeList == null)

    Office office = new Office();

    office.setGrade(grade);

    officeList = officeDao.findBranchOfficeGrade(office);

    CacheUtils.put(CAHCHE_OFFICE_GRADE_LIST+"_"+grade, officeList);

}

return officeList;
```

}

fns函数见另外笔记

items是一个Office的List，itemLabel是office的一个属性name,itemValue对应office的另一个属性id；

itemLabel是下拉框option的text属性，itemValue是option的value属性

## &lt;form:input&gt;标签

`<form:input path="applyNo" htmlEscape="false" maxlength="80" class="input-xlarge"/>`

form标签的path属性值是&lt;form:form&gt;标签的modelAttribute对象的属性；

