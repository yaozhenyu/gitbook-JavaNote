# Activiti工作流

## Activiti数据库表结构

## 概述

activiti系统一共有23个表，包括**流程定义表、一般数据信息表、流程运行实例表、流程历史记录表、用户用户组表**。

| **表分类** | **表名** | **解释** |
| :--- | :--- | :--- |
| 一般数据 | ACT\_GE\_BYTEARRAY | 通用的流程定义和流程资源 |
|  | ACT\_GE\_PROPERTY | 系统相关属性 |
| 流程历史记录 | ACT\_HI\_ACTINST | 历史的流程节点实例 |
|  | ACT\_HI\_ATTACHMENT | 历史的流程附件 |
|  | ACT\_HI\_COMMENT | 历史的说明性信息 |
|  | ACT\_HI\_DETAIL | 历史的流程运行中的细节信息 |
|  | ACT\_HI\_IDENTITYLINK | 历史的流程运行过程中用户关系 |
|  | ACT\_HI\_PROCINST | 历史的流程实例 |
|  | ACT\_HI\_TASKINST | 历史的任务实例 |
|  | ACT\_HI\_VARINST | 历史的流程运行中的变量信息 |
| 用户用户组表 | ACT\_ID\_GROUP | 身份信息-组信息 |
|  | ACT\_ID\_INFO | 身份信息-用户信息 |
|  | ACT\_ID\_MEMBERSHIP | 身份信息-用户和组关系的中间表 |
|  | ACT\_ID\_USER | 身份信息-用户信息 |
| 流程定义表 | ACT\_RE\_DEPLOYMENT | 部署单元信息 |
|  | ACT\_RE\_MODEL | 模型信息 |
|  | ACT\_RE\_PROCDEF | 已部署的流程定义 |
| 运行实例表 | ACT\_RU\_EVENT\_SUBSCR | 运行时事件 |
|  | ACT\_RU\_EXECUTION | 运行时流程执行实例 |
|  | ACT\_RU\_IDENTITYLINK | 运行时用户关系信息 |
|  | ACT\_RU\_JOB | 运行时作业 |
|  | ACT\_RU\_TASK | 运行时任务 |
|  | ACT\_RU\_VARIABLE | 运行时变量表 |



