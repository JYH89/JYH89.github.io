---
layout:     post
title:      "ReactNative项目搭建"
subtitle:   "架构工程化"
date:        2017-05-11 17:42:00
author:     ""
header-img: "img/rn_bg.jpg"
tags:
   - Jmeter
---

# ReactNative项目搭建
#### 项目流程记录
> <strong>ReactNative版本</strong> ：0.44 -> 有新版就升级<br>
> <strong> router路由搭建</strong> ：react-navigator进行管理。<br>
> <strong> 封装网络请求</strong> ：react-native-fetch-blob，其实使用fetch更加方便，但是为了防止后期涉及到的blob，还是封装了RNFetchBlob库。<br>
><strong>mock环境搭建</strong><br>
><strong>尚未接入Redux<strong><br>
><strong>Android和IOS的包名管理<strong><br>

-------

### 当前问题
> IOS打包到真机测试<br>
> IOS签名<br>
> https证书问题<br>
> IOS从其他应用入口打开<br>
> 从H5入口打开应用<br>

-------

### 在线办公问题
移动端目前查看文档的方式有三种：<br>

    1.下载文档，打开其他APP查看。<br>
    2.下载文档，使用自己App查看。（服务器将所有文档都转化成pdf，客户端做个pdf插件集成）<br>
    3.移动端通过浏览器内核打开（微信、QQ、UC），需要服务器端配置。<br>
    4.也可以不使用自己的服务器部署，使用微软或者Office的服务（可能受限，收费等问题）
<a href="http://www.cnblogs.com/yanweidie/p/4516164.html">服务器端部署参考</a><br>
<a href="https://github.com/mozilla/pdf.js/">服务器端部署pdf</a>

-------

### LBS问题
Ibeacon服务<br>
平台接入：<a href="http://www.brtbeacon.com/main/index.shtml/">智石</a> 