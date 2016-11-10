>#  ROS安装流程 #

##配置 Ubuntu 软件仓库##
配置软件仓库(repositories) 以允许 "restricted"、"universe" 和 "multiverse"这三种安装模式。 
打开Ubuntu Software Center --> Edit -->Software Sources配置

![](http://i.imgur.com/PQHDg88.png)

##添加sources.list和keys##
1.添加 sources.list
	
配置你的电脑使其能够安装来自 packages.ros.org的软件包。 ROS Jade 仅 支持Trusty (14.04)、Utopic (14.10) 和 Vivid (15.04)。

镜像可点击[http://wiki.ros.org/ROS/Installation/UbuntuMirrors](http://wiki.ros.org/ROS/Installation/UbuntuMirrors "mirror")

这里安装的时候用到了中科大的镜像源

	sudo sh -c '. /etc/lsb-release && echo "deb http://mirrors.ustc.edu.cn/ros/ubuntu/ $DISTRIB_CODENAME main" > /etc/apt/sources.list.d/ros-latest.list'
2.添加keys

    sudo apt-key adv --keyserver hkp://pool.sks-keyservers.net --recv-key 0xB01FA116

![](http://i.imgur.com/1XIpnaI.png)
##安装##
1.首先，确保你的Debian软件包索引是最新的： 

	sudo apt-get update

ROS中有四种默认安装方式


- 桌面完整版安装：（推荐） 包含ROS、rqt、rviz、通用机器人函数库、2D/3D仿真器、导航以及2D/3D感知功能。 

    `sudo apt-get install ros-jade-desktop-full`


- 桌面版安装： 包含ROS、rqt、rviz以及通用机器人函数库。 

    `sudo apt-get install ros-jade-desktop`


- 基础版安装： 包含ROS核心软件包、构建工具以及通信相关的程序库，无GUI工具。 

	`sudo apt-get install ros-jade-ros-base`


- 单个软件包安装： 你也可以安装某个指定的ROS软件包（使用软件包名称替换掉下面的PACKAGE）： 
	`sudo apt-get install ros-jade-PACKAGE`

	例如：

	`sudo apt-get install ros-jade-slam-gmapping`

	要查找可用软件包，请运行： 

	`apt-cache search ros-jade`

	本次安装的是桌面完整版,安装完成如下

![](http://i.imgur.com/xjeiTw3.png)


2.初始化rosdep

	sudo rosdep init
	rosdep update

![](http://i.imgur.com/9Hp8792.png)

![](http://i.imgur.com/tm0c70E.png)

##环境配置##

	echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
	source ~/.bashrc
如果安装有多个ROS版本, ~/.bashrc 必须只能 source 当前使用版本所对应的 setup.bash。 

如果只想改变当前终端下的环境变量，可以执行以下命令： 
	
	source /opt/ros/jade/setup.bash
##安装 rosinstall##
rosinstall 是ROS中一个独立分开的常用命令行工具，它可以方便地通过一条命令就可以给某个ROS软件包下载很多源码树。 

	sudo apt-get install python-rosinstall

![](http://i.imgur.com/y2jFt0k.png)

##Build farm 状态##
安装的各种软件包都是通过ROS build farm来编译构建的。可以在build farm查看每个软件包的编译状态。

##实验感想##
第一次安装完整版的时候，竟然死机了。然后重启之后，安装就出现了问题，试了几个网上找到的方法都无效，吃个饭重新打开ubuntu的时候竟然图形界面打不开。又试了网上的的方法尝试把图形界面搞回来，还是失败了。一气之下直接把虚拟机恢复到上学期保存的快照。
原因可能出自于在中级实训的时候，为了做的内容安装了安装教程里面说的会破坏xserver的东西。截止现在还没有解决上述问题，但是已经将该状态保存快照，在实验之后找时间解决。
