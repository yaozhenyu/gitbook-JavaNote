# Activiti工作流

## Activiti数据库表结构

## 概述

activiti系统一共有23个表，包括**流程定义表、一般数据信息表、流程运行实例表、流程历史记录表、用户用户组表**。

# 

# 一般数据

1、ACT\_GE\_BYTEARRAY（字节数据表）名称（NAME\_）、部署Id（DEPLOYMENT\_ID\_）、字节数据（BYTES\_）、发生的（GENERATED\_）

2、ACT\_GE\_PROPERTY（一般属性表）名称（NAMe\_）、值\(VALUe\_\)

# 用户用户组表

Activit 的用户用户组表，包括用户信息、用户组信息、用户与用户组间的关系、用户信息与用户之间的关系。在实际开发中未采用，用的实际系统中用户。

1、ACT\_ID\_GROUP（用户组表）名称（NAME\_）、类型\(TYPE\_\)

2、ACT\_ID\_USER（用户表）姓\(FIRST\_\)、名称\(LAST\_\)、邮件\(EMAIL\_\)、密码\(PWD\_\)、头像Id \(PICTURE\_ID\_\)

3、ACT\_ID\_INFO（用户信息表）用户Id\(USER\_ID\_\)、类型\(TYPE\_\)、formINPut名称\(KEY\_\)、值\(VALUE\_\)、密码\(PASSWORD\_\)、父节点\(PARENT\_ID\_\)

4、ACT\_ID\_MEMBERSHIP（用户用户组关联表）用户Id\(user\_ID\_\)、用户组Id（group\_Id）

#### 



