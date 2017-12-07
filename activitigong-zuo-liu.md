# Activiti工作流

## Activiti数据库表结构

## 概述

activiti系统一共有23个表，包括流程定义表、一般数据信息表、流程运行实例表、流程历史记录表、用户用户组表。

## Activiti 流程定义表

流程定义表，流程定义表也可以叫做是静态资源库，静态资源包括图片、定义规则等。它有部署信息表、流程模型表、流程定义表

1、ACT\_RE\_DEPLOYMENT（部署信息表）包括：部署流程名称、类型、部署时间

2、ACT\_RE\_MODEL（模型表）名称,key、类型、创建时间、最后修改时间、版本、数据源信息、部署ID、编辑源值ID、编辑源额外值ID（外键ACT\_GE\_BYTEARRAY ）

3、ACT\_RE\_PROCDEF（流程定义表）包括流程定义、类型、流程名称、流程key、版本号、部署ID、资源名称、图片资源名称、描述信息、是否从key启动、暂停状态。

# Activiti 运行实例表

运行实例表记录流程流转过程中产生的数据，一般数据分为两个部分流程数据、业务数据。流程数据是指activiti流程引擎流转过程中的数据，包括流程执行实例数据接、任务数据、执行任务人员信息、变量信息。业务数据则是流程过程中保存的表单数据，例如：如请假的请假单数据、报销单数据、审批意见信息等，此部分数据一般需要自己建数据表进行保存，在之前的jbpm4中没有保存业务数据。

1、ACT\_RU\_EVENT\_SUBSCR（事件子脚本）

2、**ACT\_RU\_EXECUTION（执行中流程执行）核心表 **我的代办任务查询表　流程实例ID（PROC\_INST\_ID\_），业务key（BUSINESS\_KEY\_）、父执行流程（PARENT\_ID\_）、流程定义Id（外键PROC\_DEF\_ID\_）、实例id（ACT\_ID\_）、激活状态（IS\_ACTIVE\_）、并发状态（is\_concurrent）、is\_scope、is\_evnet\_scope、暂停状态（suspension\_state）、缓存结束状态（cached\_end\_state）

3、ACT\_RU\_IDENTITYLINK（身份联系）用户组ＩＤ（GROUP\_ID\_）、用户组类型\(TYPE\_\)、用户ID\(USER\_ID\_\)、任务Id（外键：TASK\_ID\_）、流程实例ID（外键：PROC\_INST\_ID\_）、流程定义Id（外键:PROC\_DEF\_ID\_）

4、ACT\_RU\_JOB\(运行中的任务\)

5、ACT\_RU\_TASK（执行中实时任务）代办任务查询表 实例id（外键EXECUTION\_ID\_）、流程实例ID（外键PROC\_INST\_ID\_）、流程定义ID（PROC\_DEF\_ID\_）、任务名称（NAME\_）、父节任务ID（PARENT\_TASK\_ID\_）、任务描述（DESCRIPTION\_）、任务定义key（TASK\_DEF\_KEY\_）、所属人（OWNER\_）、代理人员 \(ASSIGNEE\_\)、代理团（DELEGATION\_）、优先权（PRIORITY\_）、创建时间（CREATE\_TIME\_）、执行时间（DUE\_DATE\_）、暂停状态（SUSPENSION\_STATE\_）

6、ACT\_RU\_VARIABLE（实时变量） 变量名称（NAME\_）、编码类型\(TYPE\_\)、执行实例ID\(EXECUTION\_ID\_\)、流程实例Id\(PROC\_INST\_ID\_\)、任务id\(TASK\_ID\_\)、字节组ID（BYTEARRAY\_ID\_）、DOUBLE\_、LONG\_、TEXT\_、TEXT2\_

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



