# Activiti 运行实例表

运行实例表记录流程流转过程中产生的数据，一般数据分为两个部分流程数据、业务数据。流程数据是指activiti流程引擎流转过程中的数据，包括流程执行实例数据接、任务数据、执行任务人员信息、变量信息。业务数据则是流程过程中保存的表单数据，例如：如请假的请假单数据、报销单数据、审批意见信息等，此部分数据一般需要自己建数据表进行保存，在之前的jbpm4中没有保存业务数据。

1、ACT\_RU\_EVENT\_SUBSCR（事件子脚本）

2、**ACT\_RU\_EXECUTION（执行中流程执行）核心表 **我的代办任务查询表　流程实例ID（PROC\_INST\_ID\_），业务key（BUSINESS\_KEY\_）、父执行流程（PARENT\_ID\_）、流程定义Id（外键PROC\_DEF\_ID\_）、实例id（ACT\_ID\_）、激活状态（IS\_ACTIVE\_）、并发状态（is\_concurrent）、is\_scope、is\_evnet\_scope、暂停状态（suspension\_state）、缓存结束状态（cached\_end\_state）

3、ACT\_RU\_IDENTITYLINK（身份联系）用户组ＩＤ（GROUP\_ID\_）、用户组类型\(TYPE\_\)、用户ID\(USER\_ID\_\)、任务Id（外键：TASK\_ID\_）、流程实例ID（外键：PROC\_INST\_ID\_）、流程定义Id（外键:PROC\_DEF\_ID\_）

4、ACT\_RU\_JOB\(运行中的任务\)

5、ACT\_RU\_TASK（执行中实时任务）代办任务查询表 实例id（外键EXECUTION\_ID\_）、流程实例ID（外键PROC\_INST\_ID\_）、流程定义ID（PROC\_DEF\_ID\_）、任务名称（NAME\_）、父节任务ID（PARENT\_TASK\_ID\_）、任务描述（DESCRIPTION\_）、任务定义key（TASK\_DEF\_KEY\_）、所属人（OWNER\_）、代理人员 \(ASSIGNEE\_\)、代理团（DELEGATION\_）、优先权（PRIORITY\_）、创建时间（CREATE\_TIME\_）、执行时间（DUE\_DATE\_）、暂停状态（SUSPENSION\_STATE\_）

6、ACT\_RU\_VARIABLE（实时变量） 变量名称（NAME\_）、编码类型\(TYPE\_\)、执行实例ID\(EXECUTION\_ID\_\)、流程实例Id\(PROC\_INST\_ID\_\)、任务id\(TASK\_ID\_\)、字节组ID（BYTEARRAY\_ID\_）、DOUBLE\_、LONG\_、TEXT\_、TEXT2\_

