---
title: " C++设计模式-门面模式\t\t"
tags:
  - c++
  - 设计模式
url: 831.html
id: 831
categories:
  - C/C++
date: 2017-12-27 20:40:05
---

介绍
--

*   Facade门面角色 客户端可以调用这个角色的方法。 此角色知晓子系统的所有功能和责任。 一般情况下，本角色会将所有从客户端发来的请求委派到相应的子系统去， 也就说该角色没有实际的业务逻辑， 只是一个委托类。
*   subsystem子系统角色 可以同时有一个或者多个子系统。 每一个子系统都不是一个单独的类， 而是一个类的集合。 子系统并不知道门面的存在。 对于子系统而言， 门面仅仅是另外一个客户端而已。

优点： 减少系统的相互依赖； 提高了灵活性；提高了安全性 缺点： 不符合开闭原则 应用： 为一个复杂的模块或子系统提供一个供外界访问的接口；子系统相对独立——外界对子系统的访问只要黑箱操作即可； 预防低水平人员带来的风险扩散 源码GitHub：**[CppDesignPattern](https://github.com/TechieL/CppDesignPattern)** 相关链接：[C++设计模式](http://techieliang.com/2017/12/764/)