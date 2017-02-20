###GCD的总结复习

####Runloop

- 什么是Runloop
  
  Runloop就是消息循环，每一个线程内部都有一个消息循坏。
只有主线程的消息循环默认开启，子线程的消息循环默认不开启。
消息循环的目的

保证程序不退出。负责处理输入事件。Runloop接收输入事件来自两种不同的来源：输入源(`input source`)和定时源(`timer source`)。
如果没有事件发生，会让程序进入休眠状态。
使用消息循环的时候必须指定两件事情

- 输入事件：输入源和定时源。
- 消息循环模式，此模式必须跟当前消息循环使用的模式匹配。
消息循环模式

`NSDefaultRunLoopMode。
NDRunLoopCommonModes。`子线程的Runloop,启动子线程的消息循环

--
- 并行、串行两种队列。
- 并发必定是并行，并行不一定是并发。

--
####GCD中共有三种队列
- 主队列
- 自定义队列
- 全局队列
  - 高、中、低、后台四种优先级
 
全局队列跟自定义对列的区别：

- 全局队列获取以后没有名字。有唯一性。
- 自定义队列在`MRC`基础上必须自己管理内存。


--

####GCD中队列组
--
####GCD中容易出现的问题
- 临界代码段
- 竟态条件
- 死锁
- 线程安全（GCD中的after/once都是系统安全的），反而那些平时常用的那些个方式不是线程安全的。

--
####多线程
- 主线程1M，分线程512K
- 延时操作`dispatch_after`
- 一次性执行`dispatch_once`
并非可以无限开辟，开辟越多线程死锁、竟态等等一系列多线程问题会越多。就算这些个问题不村子。速度上去了。系统开销也随之增大了。

````
dispatch_time(dispatch_time_t when, int64_t delta);
参数注释：
第一个参数：一般是DISPATCH_TIME_NOW，表示从现在开始
第二个参数：延时的具体时间

延时1秒可以写成如下几种：
NSEC_PER_SEC----每秒有多少纳秒
dispatch_time(DISPATCH_TIME_NOW, 1*NSEC_PER_SEC);
USEC_PER_SEC----每秒有多少毫秒（注意是指在纳秒的基础上）
dispatch_time(DISPATCH_TIME_NOW, 1000*USEC_PER_SEC); //SEC---毫秒
NSEC_PER_USEC----每毫秒有多少纳秒。
dispatch_time(DISPATCH_TIME_NOW。USEC_PER_SEC*NSEC_PER_USEC);
SEC---纳秒
````
####线程组
- 线程组的操作。
  - `dispatch_group_wait`阻塞当前线程；
  - `dispatch_apply`类似与`for`循环;
  - `dispatch_group_notify`线程组完成后触发通知。