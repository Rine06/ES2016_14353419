##Result##
修改后的example2的.dot文件

![](http://i.imgur.com/Krv1Bz0.png)

修改后的example1的.dot文件

![](http://i.imgur.com/SCctxN3.png)

##How to modify##
**1.修改example2**

从example2的xml代码可以看出，通过迭代定义了三个模块，通过迭代定义了三个square模块两边端点的连接情况，然后在最后两个connection里面定义了generator和第一个square以及最后一个square跟consumer之间的连接。所以，要将三个模块改成两个模块，只需要将迭代的次数减一。
即将example2.xml里面的N的大小改为2

	<variable value="2" name="N"/>

可得到结果

![](http://i.imgur.com/k7WIEco.png)


**2.修改example1**

需要将square的具体实现（square.c）中的平方改为立方即可

	i = i*i*i;

![](http://i.imgur.com/8L1HqeE.png)

##Experimental Experience##
本次实验修改的代码量很少，关键还是要从分析DOL实例的过程去理解代码，包括定义进程、对模块实现、xml的如何将模块之间连接起来等等。学习如何实现这些的语言，像是本次实验中出现的读写操作、迭代等等。

