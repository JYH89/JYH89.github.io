---
layout:     post
title:      "在cmd下使用imp命令导入oracle的dmp文件报错ORA-02304"
subtitle:   "问题排查"
date:        2018-06-20 18:21:00
author:     "RayChou"
header-img: "img/bg-sql.jpg"
tags:
   - sql
---

# oracle导入dmp文件
####报错信息如下：
```
IMP-00017: 由于 ORACLE 错误 2304, 以下语句失败:
 "CREATE TYPE "EN_CONCAT_IM" TIMESTAMP '2018-04-09:16:01:30' OID '27A29B9B634"
 "1AD1EE050FD0AD4021A7C'                                                     "
 "                                                                           "
 "                                                                           "
 " AUTHID CURRENT_USER AS OBJECT"
 "("
 "    CURR_STR VARCHAR2(32767),"
 "    STATIC FUNCTION ODCIAGGREGATEINITIALIZE(SCTX IN OUT en_concat_im) RETUR"
 "N NUMBER,"
 "    MEMBER FUNCTION ODCIAGGREGATEITERATE(SELF IN OUT en_concat_im,"
 "          P1 IN VARCHAR2) RETURN NUMBER,"
 "    MEMBER FUNCTION ODCIAGGREGATETERMINATE(SELF IN en_concat_im,"
 "                RETURNVALUE OUT VARCHAR2,"
 "                FLAGS IN NUMBER)"
 "          RETURN NUMBER,"
 "    MEMBER FUNCTION ODCIAGGREGATEMERGE(SELF IN OUT en_concat_im,"
 "         SCTX2 IN  en_concat_im) RETURN NUMBER"
 "  );"
 ""
IMP-00003: 遇到 ORACLE 错误 2304
ORA-02304: 无效的对象标识符文字
```  
#### 报这个错的原因是因为自定义type的标准创建语句是：
```
create type 变量 as table of 类型

--

create type 变量 as object(

字段1 类型1,

字段2 类型2

);
```

但是上面的sql是exp直接导出的，包含了时间戳和OID，打开PLSQL，注释掉时间戳和OID后，执行上述语句不报错，问题解决。