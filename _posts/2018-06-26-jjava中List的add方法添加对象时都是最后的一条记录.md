---
layout:     post
title:      "java中List的add方法添加对象时都是最后的一条记录"
subtitle:   "问题排查"
date:        2018-06-26 12:00:00
author:     "RayChou"
header-img: "img/bg-java.jpg"
tags:
   - java
---


 
# 测试代码

```
import java.util.ArrayList;
import java.util.List;
public class ListTest{
    public static void main(String [] args)
    {
        Cat cat1=new Cat("hello");
        Cat cat2=new Cat("java");
        Cat cat3=new Cat("world");
        List<Cat> catList=new ArrayList<>();
        catList.add(cat1);
        catList.add(cat2);
        catList.add(cat3);

        Cat cat4=new Cat();
        List<Cat> newcatList=new ArrayList<>();
        for(int j=0;j<catList.size();j++){
            cat4.setterName(catList.get(j).getterName()==null?"":catList.get(j).getterName());
            newcatList.add(cat4);
            System.out.println("NO"+j+". address in memory"+newcatList.get(j));
        }
        for(int i=0;i<catList.size();i++)
        {
            System.out.println("when define the Class Cat outside the foreach");
            System.out.print(newcatList.get(i).name);
            System.out.println();
        }
    }
}

class Cat{
    String name;
    Cat(){
        
    }
    Cat(String name){
        this.name=name;
    }
    public void setterName(String name){
        this.name =name;
    }
    public String getterName(){
        return this.name;
    }
}
```

执行结果

![](/img/20180626/ls1.png)

运行上诉代码，可以看到每次加入到list中的都是同一个对象的地址。

查看源代码
![](/img/20180626/ls2.png)


我们传递给add方法的是猫类的引用，所以传的是一个内存地址，在for循环外部定义一个对象的引用，在for循环内我们没有改变过引用的指向，
所以添加到list中的就是同一个对象的地址，如果希望传递不同的对象，则需要在for循环内部声明并创建新的猫类对象即可