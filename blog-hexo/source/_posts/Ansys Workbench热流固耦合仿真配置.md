---
title: " Ansys Workbench热流固耦合仿真配置\t\t"
tags:
  - ansys workbench
url: 100.html
id: 100
categories:
  - 其他
date: 2017-11-10 19:36:17
---

Fluent-Thermal-Structural瞬态分析-错误的方法
-----------------------------------

此模块连接在fluent已实现流体和固体的热流耦合，传递至thermal实际上只是将流体表面温度作为热载荷施加在固体的液体通道表面，极大可能导致载荷不符合情况，应直接将温度场传递至structral，取消thermal模块。

14.5版本Fluent-Structural瞬态分析-可行但复杂，需要较高人工操作或mapdl/script(python)的知识
------------------------------------------------------------------

此方案可以导入数据，但需要把每个体的每一个时间点的数据单独导入到Structural中，如果体很多且仿真结果保存步数很多，此时可以使用MAPDL操作，或者script录像（具体操作可看本博客后续文章），若手动添加消耗时间太长。 ![](http://wx3.sinaimg.cn/mw690/a8dbb8d6ly1fly4gcxwinj205508yq4n.jpg) ![需要每个体每个结果点都导入](http://wx3.sinaimg.cn/mw690/a8dbb8d6ly1fly4gcxwinj205508yq4n.jpg)

> 此方案在18.0版本可以自动添加所有时间点结果，只需要分别导入每个体的第一个时间点即可

14.5版本Fluent-Structural双向耦合-不可行，但18.0版本可行
-----------------------------------------

此版本Fluent-Structural双向耦合，只支持Fluent的流体力数据导入到Structural，无法导入温度信息，此方案不可用，但是在18.0版本可以实现热参数的传递，可以完成热流固耦合。14.5版本结果如下图： ![](http://wx4.sinaimg.cn/mw690/a8dbb8d6ly1fly4gdem3gj20fe04ot9n.jpg) ![](http://wx1.sinaimg.cn/mw690/a8dbb8d6ly1fly4gduvkjj205u093my8.jpg)

> 此方案在18.0版本中可行，好像是从17.0版本就支持了双向耦合过程的温度信息传递

上述均再考虑如何把热流耦合的计算得到的温度场信息导入结构的方法，下面说一下热流耦合的实现方法： 直接用Fluent肯定是最省事的，但是Fluent对于结构参数的配置很复杂，而且Fluent 对于体很多的情况加载很慢计算速度也明显下降。同样的结构若把流体和结构分析分成两部分别在Fluent和thermal进行分析，效率会高很多

> 注意：14.5版本版本不支持Fluent与Thermal瞬态模块的双向耦合。。。。18.0可以，建议用高版本