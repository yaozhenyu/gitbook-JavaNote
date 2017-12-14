# BPMN

**BPMN四种基本元素是：**

* 流对象（Flow Objects）

  1、事件（Event\):  Event 用一个圆圈表示，它是流程中运行过程中发生的事情。事件的发生会影响到流程的流转.事件包含Start\Intermediate\End三种类型

  ![](/assets/bpmn_event.png)

  2、活动（Activity）

  活动用圆角矩形表示，一个活动多个活动组成，活动的类型分为Task和Sub-Process。如下下图：![](/assets/bpmn_activity.png)

  3、网关（Gateway）：用菱形表示，用来控制流程的分支和聚合，在本文中常用的是“互斥关口”，表示后续分支只能选择一条路线进行任务流转

  ![](/assets/bpmn_gateway.png)

* 连接对象（Connecting Object\)

  1、Sequence Flow，序列流： 用实线实心箭头（实线+实心三角箭头）表示，代表流程中将被执行的活动的执行顺序

  2、Message Flow，消息流：用虚线空心箭头（虚线+空心三角箭头）表示，用来表示2个分开的流程参与者（业务实体或业务角色）之间发送或者接收到的消息流

  3、Association，关联： 点状虚线（-------〉）表示，用于显示活动的输入输出

* 泳道（Swimlanes）

* 附件（Artifacts）



