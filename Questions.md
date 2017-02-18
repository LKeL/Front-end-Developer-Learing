#Front-end-Developer-Interview-Questions Answer

> [原题目的github地址](https://github.com/h5bp/Front-end-Developer-Interview-Questions)

## General Questions

##### What did you learn yesterday/this week?(你在昨天/本周学到了什么？)

当前时间2017-2-18 周六，过去五天学习了pixijs，一个轻量级的使用WebGL的HTML5 2D渲染引擎，原因是看到[这样一个问题](http://stackoverflow.com/questions/36908427/webgl-vs-canvas-2d-hardware-acceleration)，想要弄清楚当下移动端浏览器canvas 2d和webgl在实际项目中渲染效率区别

#####What excites or interests you about coding?(编写代码的哪些方面能够使你兴奋或感兴趣？)

学习新技术的过程，编程时思考的过程，造出的轮子被人使用，自己设想的种种意外情况都被自己的程序给巧妙地处理了，看着这样的作品会觉得很美妙，创造一个东西很开心啊

#####What is a recent technical challenge you experienced and how did you solve it?（你最近遇到过什么技术挑战？你是如何解决的？）

是我所做的毕业设计（面向少年的机器人简易图形化编程工具设计与实现），问题所在是如何实现运行实时暂停继续功能，因为所呈现的应是一个功能区块的暂停而不是一行代码的断点（比如机器人有前进和抬手两个并行任务，实现手抬一半暂停但机器人仍然前进，前进结束后继续抬手），首先想到的实现类似redis的事件轮询，考虑之后可能加入的功能（比如环境感知），因此需要加入事件优先权，即实现多级反馈队列调度，需要暂停的任务直接开中断将该任务权值设为-1阻塞掉，这样就不用考虑上下文问题，产生的新问题是控制器发送暂停指令到机器执行所产生的误差，即运动停止，最后的实际发现即使外接中断指令接收信号器，产生的误差远远小于所买的几百块的机械臂产生的误差
#####What UI, Security, Performance, SEO, Maintainability or Technology considerations do you make while building a web application or site?（在制作一个网页应用或网站的过程中，你是如何考虑其 UI、安全性、高性能、SEO、可维护性以及技术因素的？）



