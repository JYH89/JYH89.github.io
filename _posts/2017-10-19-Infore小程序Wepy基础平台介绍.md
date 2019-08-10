---
layout:     post
title:      "盈峰小程序Wepy框架"
subtitle:   "基于Wepy框架，Vue语法开发，build成小程序和Web页面。"
date:        2017-10-09 17:20:00
author:     "mifind"
header-img: "img/wei-xcx.jpeg"
tags:
   - sql
---

# 盈峰微信小程序框架
* 框架基于Wepy框架，WePY是一款让小程序支持组件化开发的框架，通过预编译的手段让开发者可以选择自己喜欢的开发风格去开发小程序。框架的细节优化，Promise，Async Functions的引入都是为了能让开发小程序项目变得更加简单，高效。
* 该框架给小程序提供了开发的新思路，走出原生的架构，Vue语法与双向绑定思路，使前端开发人员也可以更短时间接受小程序的开发思路。
* <strong>代码写的规范，完全可以使用一套代码应用在微信小程序和Web双平台！！！</strong>

#### WePY资源汇总：[awesome-wepy](https://github.com/aben1188/awesome-wepy)

### 框架特性：
* 类Vue开发风格
* 支持自定义组件开发
* 支持引入NPM包
* 支持[Promise](https://github.com/wepyjs/wepy/wiki/wepy%E9%A1%B9%E7%9B%AE%E4%B8%AD%E4%BD%BF%E7%94%A8Promise)
* 支持ES2015+特性，如[Async Functions](https://github.com/wepyjs/wepy/wiki/wepy%E9%A1%B9%E7%9B%AE%E4%B8%AD%E4%BD%BF%E7%94%A8async-await)
* 支持多种编译器，Less/Sass/Styus、Babel/Typescript、Pug
* 支持多种插件处理，文件压缩，图片压缩，内容替换等
* 支持 Sourcemap，ESLint等
* 小程序细节优化，如请求列队，事件优化等

## Mock-api集成
* 在server文件夹中有一个infore.json，根据规则配置出mock-api。
* 通过mock-api serve **/_dir目录/server开启mock服务。
* mock服务的默认地址：localhost:10086


# 项目布局

```
├── dist                   微信开发者工具指定的目录
├── web                    web页面生成目录
├── node_modules           
├── src                    代码编写的目录
|   ├── components         组件、页面文件夹
|   |   ├── widget         可复用组件
|   |   └── pages          完整页面
|   ├── core               与业务UI无关的核心代码（api、配置）
|   ├── images             图片
|   ├── style              公共样式、WeUI组件
|   └── app.wpy            小程序配置项（全局样式配置、声明钩子等）
├── index.template.html    模板页面html
└── package.json           package 配置
```
### 安装使用

#### 安装（更新） wepy 命令行工具。

```console
npm install wepy-cli -g
```

#### 生成开发示例

```console
wepy new myproject
```

#### 开发实时编译

```console
wepy build --watch
```

#### 开发者工具使用

1. 使用`微信开发者工具`新建项目，本地开发选择`dist`目录。
2. `微信开发者工具`-->项目-->关闭ES6转ES5。<font style="color:red">重要：漏掉此项会运行报错。</font>
3. `微信开发者工具`-->项目-->关闭上传代码时样式自动补全 <font style="color:red">重要：某些情况下漏掉此项会也会运行报错。</font>
4. `微信开发者工具`-->项目-->关闭代码压缩上传 <font style="color:red">重要：开启后，会导致真机computed, props.sync 等等属性失效。[#270](https://github.com/wepyjs/wepy/issues/270)</font>
5. 项目根目录运行`wepy build --watch`，开启实时编译。
*  项目根目录运行`wepy build --output web`，编译成web文件。



### 已经开源，见这里见这里~
[infore-wepy-base](https://github.com/MIFind/infore-wepy-base)
