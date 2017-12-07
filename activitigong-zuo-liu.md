# Activiti工作流

## Activiti数据库表结构

## 概述

activiti系统一共有23个表，包括**流程定义表、一般数据信息表、流程运行实例表、流程历史记录表、用户用户组表**。

| **表分类** | **表名** | **解释** |
| :--- | :--- | :--- |
| 一般数据 | [ACT\_GE\_BYTEARRAY](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_GE_BYTEARRAY) | 通用的流程定义和流程资源 |
|  | [ACT\_GE\_PROPERTY](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_GE_PROPERTY) | 系统相关属性 |
| 流程历史记录 | [ACT\_HI\_ACTINST](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_HI_ACTINST) | 历史的流程实例 |
|  | [ACT\_HI\_ATTACHMENT](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_HI_ATTACHMENT) | 历史的流程附件 |
|  | [ACT\_HI\_COMMENT](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_HI_COMMENT) | 历史的说明性信息 |
|  | [ACT\_HI\_DETAIL](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_HI_DETAIL) | 历史的流程运行中的细节信息 |
|  | [ACT\_HI\_IDENTITYLINK](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_HI_IDENTITYLINK) | 历史的流程运行过程中用户关系 |
|  | [ACT\_HI\_PROCINST](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_HI_PROCINST) | 历史的流程实例 |
|  | [ACT\_HI\_TASKINST](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_HI_TASKINST) | 历史的任务实例 |
|  | [ACT\_HI\_VARINST](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_HI_VARINST) | 历史的流程运行中的变量信息 |
| 用户用户组表 | [ACT\_ID\_GROUP](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_ID_GROUP) | 身份信息-组信息 |
|  | [ACT\_ID\_INFO](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_ID_INFO) | 身份信息-组信息 |
|  | [ACT\_ID\_MEMBERSHIP](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_ID_MEMBERSHIP) | 身份信息-用户和组关系的中间表 |
|  | [ACT\_ID\_USER](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_ID_USER) | 身份信息-用户信息 |
| 流程定义表 | [ACT\_RE\_DEPLOYMENT](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_RE_DEPLOYMENT) | 部署单元信息 |
|  | [ACT\_RE\_MODEL](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_RE_MODEL) | 模型信息 |
|  | [ACT\_RE\_PROCDEF](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_RE_PROCDEF) | 已部署的流程定义 |
| 运行实例表 | [ACT\_RU\_EVENT\_SUBSCR](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_RU_EVENT_SUBSCR) | 运行时事件 |
|  | [ACT\_RU\_EXECUTION](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_RU_EXECUTION) | 运行时流程执行实例 |
|  | [ACT\_RU\_IDENTITYLINK](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_RU_IDENTITYLINK) | 运行时用户关系信息 |
|  | [ACT\_RU\_JOB](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_RU_JOB) | 运行时作业 |
|  | [ACT\_RU\_TASK](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_RU_TASK) | 运行时任务 |
|  | [ACT\_RU\_VARIABLE](file:///C:/Users/Administrator/Desktop/Activiti%E5%B7%A5%E4%BD%9C%E6%B5%81%E6%95%B0%E6%8D%AE%E5%BA%93%E8%A1%A8%E7%BB%93%E6%9E%84.docx#LOCAL_1-ACT_RU_VARIABLE) | 运行时变量表 |



