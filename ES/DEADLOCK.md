>#  DEADLOCK #

##死锁的四个必要条件##
- Mutual exclusion：only one process at a time can use a resource.
- Hold and wait: a process holding at least one resource is waiting to acquire additional resources held by other processes.
- No preemption: a resource can be released only voluntarily by the process holding it, after that process has completed its task.
- Circular wait: there exists a set {P0, P1, …, P0} of waiting processes such that P0 is waiting for a resource that is held by P1, P1 is waiting for a resource that is held by P2, …, Pn–1 is waiting for a resource that is held by Pn, and P0 is waiting for a resource that is held by P0.

##程序解释##
定义了一个Deadlock类，在这个类里面涉及到了两个类A和B。这两个类在调用method的时候都会调用另一个函数里面的last函数。
死锁的发生过程：
主函数创建新的类Deadlock(),然后随之在里面分别创建类A和B的对象a以及b。
接着创建了一个新的线程t。t.start()之后，线程t被插入到调度队列里面，当调度到它的时候就跑run()里面的代码。
runnable运行是调用run()函数，线程b调用methodB函数，由于synchronized关键字的约束，在b占用了类B的methodB之后，其他线程对类B里面所有的同步代码块或同步方法的访问都将被阻塞。在methodB里面调用了a的last()函数。
也就是说,b占用了methodB,想去申请a的last()
同理，a占用了methodA,想去申请b的last()
由于这两个进程具有相同的优先级，所以会进入循环等待当中。
满足了互斥（同步块），非抢占（优先级相同），占有且等待（b占有了methodB等待a.last(),a占有了methodA等待b.last()）以及循环等待，死锁产生。

##结果截图##
count==2000

![](http://i.imgur.com/3jc12Xk.png)

count==5000

![](http://i.imgur.com/VCELViT.png)

count==20000

![](http://i.imgur.com/N1h9f1N.png)

count==50000

![](http://i.imgur.com/Pc95OQs.png)