---
layout:     post
title:      "关于移动前端技术栈Vue和React的思考"
subtitle:   "about webapp"
date:        2017-03-27 09:00:00
author:     "mifind"
header-img: "img/vue-mvvm.png"
tags:
   - java
---



# 关于移动前端技术栈Vue和React的思考

### 本篇：
         1.Vue作为一款优秀的MVVM前端框架的技术思想与思考。
         2.和React的对比。

## 一、Vue作为一款优秀的MVVM前端框架的技术思想与思考。

    首先Vue.js 是一个轻量级的前端 MVVM 框架，专注于web视图(View)层的开发 。但是大多数前端开发者都是通过jQuery入门，因为jQuery我也只是有用过，但是使用期间的问题还是有的，我们不可否认jQuery简化了DOM的操作，但是我们还是会把精力集中在DOM的操作与数据更新，大量的DOM操作使得一个库变得逻辑非常繁琐，扩展性和维护性都会变得很差。

    所以，Vue作为专注于操作Model的MVVM框架的，可以做到视图与数据同步，不需要人为干预，这种Observer模式，不论是在前端还是在Native都是逐渐被开发者认可。

    通过 ViewModel 对 View 和 Model 进行桥接，而Model 和 ViewModel 之间的交互是双向的，View 数据的变化会同步到 Model 中，Model 中的数据变化也会立即反应到 View 上，即我们通常所说的「双向绑定」。这是不需要人为干涉的，所以开发者只需要关注业务逻辑，其他的DOM操作、状态维护等都由MVVM框架来实现。

![](/img/vue-mvvm.png)

            下图是在官网down来的，可以有一个简单的认识，相对于React的state即View的思路，Vue通过指令进行View与Model的关联，比如{{msg}}、v-bind，指令如何操作DOM，设计的问题也很复杂：
                 1）如何正确解析混在Vue template中(html)的指令(Directives)和表达式。
                 2）不同的指令如何对应不同的DOM更新方式。
                 3）如何绑定数据，绑定的数据更新时如何快速通知DOM进行更新。
看到这里大家应该都能想到其实核心思想一定是使用了观察者模式。

![](/img/vue-mvvm1.png)
（截图来自百度外卖前端）

    我们在上面的途中可以看到大致思路，在初始化视图时，Observer获取data数据，并通过Object.defineProperty实现双向数据绑定（原谅我还没有深入研究），Compiler 对DOM节点指令进行扫描和解析，并订阅Watcher 来更新视图。在更新阶段，当数据变更时，会触发 setter 函数，立即会触发相应的通知, 开始遍历所有订阅者，调用其指令的update方法，进行视图更新。
            这样就将焦点聚焦在：
            1）Observer如何实现数据绑定（如何通过代理整个DOM树的data，并进行defineProperty实现数据绑定）。
            2）Compiler如何解析Templete，并执行底层相应函数。
            3）Watcher订阅者如何订阅到所有Model的变化并执行对应的指令绑定函数。
            这里面涉及的Vue状态机思想，确实太复杂了，研究一时半会确实无法看痛，付一张勾股大神的原理图，大家感受一下。

![](/img/vue-state.png)

## 二.Vue和React对比

#### 对比一下Vue和React，还有Native，我们来谈一下我心中的移动开发的趋势。

* VirtualDOM，这个概念绝对是WebApp越来越受欢迎的关键，通过JS对象模拟DOM，因为JS对象相对于原生DOM的性能要提升很多，原生DOM的解析与处理都是相当庞大的，想想我们当初写getDocumentById来获取DOM节点操作DOM，这种遍历的速度，是无法适应移动端频繁的页面刷新速度。加上DOM Diff 极大提升了DOM操作的性能。

* 对于React来说，JSX的使用方式和templent并没有优劣之分，而且Vue2.0后Vue也支持的JSX的语法。有人说React门槛高，这也是相对的来说，对于小白来说React全家桶确实有一些多。
        Vue入手并不需要太多的改变，学会指令和思路，还是去开发你的html，数据绑定框架解决，入手非常容易，而且后续推出的vue-router，vue-touch，以及vuex（对应Redux）都是很简单。但是但是其实ES6，函数式编程，JSX，Redux，工程化构建这些东西对于一个开发者并不是太难的东西。
* 我觉得其实对于Vue的喜欢不再其渲染速度，而是相比于React来说Vue最让我舒服的一点是Vue不需要像React 那样去手动声明shouldComponentUpdate 来优化状态变更时的重新渲染的性能。
        可能是我React研究的也不深吧。
