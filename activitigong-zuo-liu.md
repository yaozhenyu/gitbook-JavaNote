# Activiti工作流

## Activiti数据库表结构

## 概述

activiti系统一共有23个表，包括**流程定义表、一般数据信息表、流程运行实例表、流程历史记录表、用户用户组表**。

# 

# 流程历史记录

流程历史信息表，activiti历史记录表包括节点信息表、附件信息表、历史审批记录表、理想详细信息表、历史身份信息表、流程实例历史表、任务历史表、历史变量表。（节点信息表、附件信息表、历史审批记录表、理想详细信息表、历史身份信息表）这些表目前还未知是如何用的。（流程实例历史表、任务历史表、历史变量）三个表可以查询我已完成任务、任务追踪等。

1、**ACT\_HI\_ACTINST（活动实例信息）**流程定义ID（PROC\_DEF\_ID\_）、流程实例ID（PROC\_INST\_ID\_）、流程执行ID（EXECUTION\_ID\_）、活动ID（ACT\_ID\_）、活动名称（TASK\_ID\_）、活动类型（ACT\_TYPE\_）、任务ID、（TASK\_ID\_）、请求流程实例ID（CALL\_PROC\_INST\_ID\_）、代理人员（ASSIGNEE\_）、开始时间（START\_TIME\_）、结束时间\(END\_TIME\_\)、时长（DURATION\_）

2、ACT\_HI\_ATTACHMENT（附件信息）用户id（USER\_ID\_）、名称（NAME\_）、描述（DESCRIPTION\_）、类型（TYPE\_）、任务Id（TASK\_ID\_）、流程实例ID（PROC\_INST\_ID\_）、连接（URL\_）、内容Id（CONTENT\_ID\_）

3、ACT\_HI\_COMMENT（历史审批信息）类型（TYPE\_）、时间（TIME\_）、用户Id（USER\_ID\_）、任务Id（TASK\_ID\_）、流程实例Id（PROC\_INST\_ID\_）、活动（ACTION\_）、消息（MESSAGE\_）、全部消息（FULL\_MSG\_）

4、ACT\_HI\_DETAIL（历史详细信息）数据类型（TYPE\_）、创建时间\(TIME\_\)、名称\(NAME\_\)、流程实例ID（PROC\_INST\_ID\_）、执行实例Id\(EXECUTION\_ID\_\)、任务Id\(TASK\_ID\_\)、活动实例Id\(ACT\_INST\_ID\_\)、变量类型\(VAR\_TYPE\_\)、字节数组Id、DOUBLE\_、LONG\_、值（TEXT\_）、值2（TEXT2\_）

5、ACT\_HI\_IDENTITYLINK（历史身份信息）任务Id（TASK\_ID\_）、流程实例Id（PROC\_INST\_ID\_）、userId（USER\_ID\_）、用户组类型Type（TYPE\_）、用户组ID（GROUP\_ID\_）

6、**ACT\_HI\_PROCINST（历史流程实例信息）核心表**　流程实例ID（PROC\_INST\_ID\_）、业务Key（BUSINESS\_KEY\_）、流程定义Id（PROC\_DEF\_ID\_）、开始时间（START\_TIME\_）、结束时间（END\_TIME\_）、时长（DURATION\_）、发起人员Id（START\_USER\_ID\_）、开始节点（START\_ACT\_ID\_）、结束节点（END\_ACT\_ID\_）、超级流程实例Id（SUPER\_PROCESS\_INSTANCE\_ID\_）、删除理由（DELETE\_REASON\_）

7、**ACT\_HI\_TASKINST（历史任务流程实例信息）核心表**　流程实例ID（PROC\_INST\_ID\_）、任务定义Key（BUSINESS\_KEY\_）、流程定义Id（PROC\_DEF\_ID\_）、执行ID（EXECUTION\_ID\_）、名称（NAME\_）、父任务iD（PARENT\_TASK\_ID\_）、描述（DESCRIPTION\_）、所属人（OWNER\_）、代理人（ASSIGNEE\_）、开始时间（START\_TIME\_）、结束时间（END\_TIME\_）、时长（DURATION\_）、删除理由（DELETE\_REASON\_\_）、优先级（PRIORITY\_）、应完成时间（DUE\_DATE\_）、表单key（FORM\_KEY\_）

8、ACT\_HI\_VARINST（历史变量信息）流程实例ID（PROC\_INST\_ID\_）、执行ID（EXECUTION\_ID\_）、任务Id、名称（NAME\_）、变量（TASK\_ID\_）、类型（VAR\_TYPE\_）、字节数组ID（BYTEARRAY\_ID\_）、DOUBLE\_、LONG\_、TEXT\_、TEXT2\_

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



