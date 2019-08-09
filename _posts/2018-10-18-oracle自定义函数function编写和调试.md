---
layout:     post
title:      "oracle自定义函数function编写和调试"
subtitle:   "参数化-脚本生成"
date:        2018-10-18 17:20:00
author:     "RayChou"
header-img: "img/infore-cli.jpeg"
tags:
   - Jmeter 
---
# oracle自定义函数function编写和调试
关于function的书写格式如下：
自定义函数语法:
```
CREATE OR REPLACE FUNCTION 函数名
RETURN 返回值类型
IS
声明部分;
BEGIN
函数体;
RETURN 变量;
END;
```

### 下面是我写的一个关于生成带特殊前缀的自增ID的函数

```
create or replace function getemailmodeID(pre in varchar) return varchar as
  emailID varchar(32);
  v_pre varchar2(32);
begin
    v_pre :=pre;
    execute immediate 'select trim('''||v_pre||''')||lpad(sqn_emailmode.nextval,8,''0'')  from dual' into emailID;
    return emailID;
end getemailmodeID;
```


## 另外在书写过程中可以使用PLSQL自带的调试功能，如下图：
#1）选中具体的函数，邮件选择test
![](/img/20190101/f1.png)
#2)输入变量，既可以执行函数
![](/img/20190101/f2.png)










