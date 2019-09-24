---
layout:     post
title:      "理解HttpServletResponse中的setHeader()和addHeader()的区别"
subtitle:   "代码调试"
date:        2018-06-28 07:42:00
author:     ""
header-img: "img/bg-java.jpg"
tags:
   - java
---

#### 调试流程记录
首先看下使用addHeader方法添加两个完全一样的信息：
 
 response.addHeader("foo","beer");
 response.addHeader("foo","beer");

![](/img/20180628/ts1.png)

接下来看下使用addHeader方法添加两个名字相同，值不同的情况

response.addHeader("foo","bar");
response.addHeader("foo","beer");
![](/img/20180628/ts2.png)

以上可以得知addHeader方法总是为响应增加新的首部。

接下来看下setHeader()添加两个完全一样的信息：

response.setHeader("foo","beer");
response.setHeader("foo","beer");
![](/img/20180628/ts3.png)

最后来看下使用setHeader方法添加两个名字相同，值不同的情况

response.setHeader("foo","bar");
response.setHeader("foo","beer");
![](/img/20180628/ts4.png)

以上可以得知setHeader方法总是用新值去替换旧值。 