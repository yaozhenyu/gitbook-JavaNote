# 

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

# Jquery-validate

## 导入 js 库

```
<script src="http://static.runoob.com/assets/jquery-validation-1.14.0/lib/jquery.js"></script>
<script src="http://static.runoob.com/assets/jquery-validation-1.14.0/dist/jquery.validate.min.js"></script>
<script src="http://static.runoob.com/assets/jquery-validation-1.14.0/dist/localization/messages_zh.js"></script>
```

jQuery Validate提供了中文信息提示包，位于下载包的 dist/localization/messages\_zh.js

```
$().ready(function() {
// 在键盘按下并释放及提交后验证提交表单
  $("#signupForm").validate({
    rules: {
      firstname: "required",
      lastname: "required",
      username: {
        required: true,
        minlength: 2
      },
      password: {
        required: true,
        minlength: 5
      },
      confirm_password: {
        required: true,
        minlength: 5,
        equalTo: "#password"
      },
      email: {
        required: true,
        email: true
      },
      topic: {
        required: "#newsletter:checked",
        minlength: 2
      },
      agree: "required"
    },
    messages: {
      firstname: "请输入您的名字",
      lastname: "请输入您的姓氏",
      username: {
        required: "请输入用户名",
        minlength: "用户名必需由两个字母组成"
      },
      password: {
        required: "请输入密码",
        minlength: "密码长度不能小于 5 个字母"
      },
      confirm_password: {
        required: "请输入密码",
        minlength: "密码长度不能小于 5 个字母",
        equalTo: "两次密码输入不一致"
      },
      email: "请输入一个正确的邮箱",
      agree: "请接受我们的声明",
      topic: "请选择两个主题"
     }
    })
});



$().ready(function() {
     $("#signupForm").validate({
        submitHandler:function(form){
            alert("提交事件!");   
            form.submit();
        }    
    });
});
```

### 添加自定义校验

```
addMethod：name, method, message
```

自定义验证方法

```
// 中文字两个字节
jQuery.validator.addMethod("byteRangeLength", function(value, element, param) {
    var length = value.length;
    for(var i = 0; i < value.length; i++){
        if(value.charCodeAt(i) > 127){
            length++;
        }
    }
  return this.optional(element) || ( length >= param[0] && length <= param[1] );   
}, $.validator.format("请确保输入的值在{0}-{1}个字节之间(一个中文字算2个字节)"));

// 邮政编码验证   
jQuery.validator.addMethod("isZipCode", function(value, element) {   
    var tel = /^[0-9]{6}$/;
    return this.optional(element) || (tel.test(value));
}, "请正确填写您的邮政编码");
```

**注意**：要在 additional-methods.js 文件中添加或者在 jquery.validate.js 文件中添加。建议一般写在 additional-methods.js 文件中。

**注意**：在 messages\_cn.js 文件中添加：isZipCode: "只能包括中文字、英文字母、数字和下划线"。调用前要添加对 additional-methods.js 文件的引用。

