---
title: 概述
description: 本页面是对软件各类脚本函数的汇总，为适应数值计算的需要，软件内置了丰富的脚本函数。
keywords: 脚本函数库,数值计算,仿真脚本,矩阵计算,数据可视化
businessId: Script-Commands_script-commands-overview 
language: zh-CN
sort: 20
published: true
date: 2023-08-23T03:21:28.789Z
tags: 脚本
editor: markdown
dateCreated: 2023-04-11T01:55:45.825Z
---

**本页面是对软件脚本函数的汇总**。

**为适应数值计算的需要，软件内置了丰富的脚本函数。**


# 基本语法
基本语法包括：
- [变量和常量](/localhost/knowledge-base/Script-Commands_script-variables)，脚本变量的定义以及使用说明，包括数字，字符串，结构体，软件的数据集等的创建方式及相关操作指令；
- [数据的导入和导出](/localhost/knowledge-base/Script-Commands_data-input-and-output)，脚本初始化，数据的保存、导入和导出；
- [程序控制流程](/localhost/knowledge-base/Script-Commands_program-control-flow)，包括用于实现分支结构、循环结构等流程控制结构的函数；
- [基本操作](/localhost/zh-CN/knowledge-base/Script-Commands_basic-operations)，各种与变量和文件相关的基本操作，例如查询变量类型、查询变量的成员、切换工作目录；
- [函数](/localhost/knowledge-base/Script-Commands_functions)，自定义函数的使用和说明，同时还介绍了与远场分析和色度学分析相关的函数；
- [基础数学](/localhost/zh-CN/knowledge-base/Script-Commands_basic-maths)，三角函数、对数函数、指数函数、幂函数等各类基本初等函数以及求绝对值、求实、虚部等基础的数学操作；
- [高等数学](/localhost/zh-CN/knowledge-base/Script-Commands_advanced-maths)，包括用于微积分计算、傅里叶分析和插值等高等数学运算的函数；
- [矩阵运算](/localhost/zh-CN/knowledge-base/Script-Commands_matrix-calculations)，包括基本的矩阵操作和与求解矩阵方程相关的函数。

# 数据获取
[数据获取](/localhost/knowledge-base/Script-Commands_getting-data)函数包括：
- 查询获取命令：列出所选对象的所有结果数据的名称；
- 查询所选对象是否含有所需的数据；
- 获取求解器、光源等对象的某一属性的值；
- 从光源、监视器或分析组获取结果。


# 对象设置
[对象设置](/localhost/knowledge-base/Script-Commands_setting-objects)函数用以添加对象、设置对象、操作对象以及材料的添加和设置：
- 添加对象：结构、光源、监视器、结构组、分析组等的添加；
- 查询设置命令：返回所选对象的属性列表；
- 设置对象：对结构、光源、监视器、结构组、分析组等的参数进行设置；
- 操作对象：对所选对象进行视图转换、固定、隐藏和删除等操作；
- 添加和设置材料：添加所需材料，并设置材料参数。

# 仿真
[仿真](/localhost/knowledge-base/Script-Commands_simulation)函数主要用以设置工程仿真相关的参数和控制工程的运行：
- 仿真参数设置；
- 控制仿真：控制工程的运行；
- 解模：在模式源中求解模式；
- 添加自定义网格；
- 前处理和后处理相关的函数，如控制分析组脚本运行的函数。

# 数据可视化
[数据可视化](/localhost/knowledge-base/Script-Commands_data-visualization)的脚本命令，包括：
- 不同类型的绘图函数；
- 对应可视化窗口的命令，绘图结果的修饰。

# 杂项
[杂项](/localhost/knowledge-base/Script-Commands_miscellaneous)包括：
- 工作区内的各种操作: 在脚本工作区中，用户可以借助GUI对现有的变量执行诸如打印、绘制等基本操作。

