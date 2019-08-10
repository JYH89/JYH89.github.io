---
layout:     post
title:      "盈峰环境基础组建平台开发（旧）"
subtitle:   "关于如何组织主项目和组件包的版本依赖"
date:        2017-08-31 17:20:00
author:     "mifind"
header-img: "img/rn_bg.jpg"
tags:
   - sql
---


## InforeEnviro 基础组建平台开发

> * 新项目开发流程
* 主项目和lib项目版本管理
* 应用分析

--

### 新项目开发流程
1. git clone 模板项目
2. 更改bower.json引用。
3. 执行bower，从gitlab取到相关版本的组件。
4. 代码中使用组件。


--
### 主项目和lib项目版本管理
* 版本强依赖。
* 举例：主版本1.0依赖拍照模块2.0，过一阵拍照模块代码更新到2.1，重新down代码，下载的依然是bower依赖的拍照2.0版本，不会有影响。

> 主项目中更改了lib代码，同步到gitlab库，打tag，依赖新版本。

--
### 应用分析
* 通过bower来管理gitlab中的包。
* 组件尽量拆分地细粒度，一个组件或者一类组件放在一个git仓库里。相近范畴和功能的组件在一个git仓库里。


![](/img/rn0831.jpeg)
