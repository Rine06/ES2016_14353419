## Description ##
**The distributed operation layer (DOL)** is a framework that enables the (semi-) automatic mapping of applications onto the multiprocessor SHAPES architecture platform. The DOL consists of basically three parts:

- **DOL Application Programming Interface**: The DOL defines a set of computation and communication routines that enable the programming of distributed, parallel applications for the SHAPES platform. Using these routines, application programmers can write programs without having detailed knowledge about the underlying architecture. In fact, these routines are subject to further refinement in the hardware dependent software (HdS) layer.
- **DOL Functional Simulation**: To provide programmers a possibility to test their applications, a functional simulation framework has been developed. Besides functional verification of applications, this framework is used to obtain performance parameters at the application level.
- **DOL Mapping Optimization**: The goal of the DOL mapping optimization is to compute a set of optimal mappings of an application onto the SHAPES architecture platform. In a first step, XML based specification formats have been defined that allow to describe the application and the architecture at an abstract level. Still, all the information necessary to obtain accurate performance estimates is contained.

## How to install ##
The DOL runs under UNIX/Linux as well as under Microsoft Windows.The process below runs under UNIX/Linux just for an example.

**1.Install Required Environments**

	$	sudo apt-get update

	$	sudo apt-get install ant

	$ 	sudo apt-get install openjdk-7-jdk

	$	sudo apt-get install unzip

**2.Download**

	sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz

	sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip

**3.Unzip**

create a new Folder named "dol"

	$	mkdir dol

unzip dolethz.zip to folder dol

	$	unzip dol_ethz.zip -d dol

unzip systemc

	$	tar -zxvf systemc-2.3.1.tgz

**4.Compile Systemc**

open the path of systemc-2.3.1

	$	cd systemc-2.3.1

create a new folder objdir

	$	mkdir objdir

open objdir

	$	cd objdir

configure

	$	../configure CXX=g++ --disable-async-updates
you will see

![](http://i.imgur.com/Y06Nd8c.png)

then compile

	$	sudo make install

list files

	$ cd #your path of systemc 
	$ ls

![](http://i.imgur.com/iGvH5j9.png)

record the current path

	pwd

![](http://i.imgur.com/agpKRWn.png)

it shows that my current path is "/home/rin/systemc-2.3.1
"

**5.Compile DOL**

open the folder dol we create before

	$	cd ../dol

modify build_zip.xml

	$	gedit build_zip.xml

find

	<property name="systemc.inc" value="YYY/include"/>
	<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>

change YYY to the result of pwd

**attention**:for **64 bits system**,lib-linux should be modified to **lib-linux64** 

then compile
	
	$	ant -f build_zip.xml all

if success,you will see build success

![](http://i.imgur.com/DYiBZeg.png)

now,we can try to run the first example

Firstly,open path build/bin/main in folder dol

	$	cd build/bin/main

![](http://i.imgur.com/pqtiU6I.png)

run the 1st example
	
	$	ant -f runexample.xml -Dnumber=1

if success

![](http://i.imgur.com/vEXHZKR.png)

to check the dot file,you should firstly install xdot

	$	sudo apt-get install xdot

open file example1.dot

 ![](http://i.imgur.com/apamObw.png)

## Experimental Experience ##
配置DOL的过程，跟着教程走很顺利，中间基本上没有大的问题。对DOL，看了DOL的PDF文档还有课件，有了一些概念上的了解，但是还没有深入学习理解，在接下来的实验中需要从实践去加深。
