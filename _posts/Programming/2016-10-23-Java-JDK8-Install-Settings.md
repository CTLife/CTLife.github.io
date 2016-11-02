---
layout: post
title: Java JDK 8 的安装以及环境变量的配置(Linux and Windows)
category: Programming
tags: Java  安装配置
keywords: 
description: 
---

JDK(Java Development Kit)包括了Java语言的编译器，可以在这里下载：

[http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) 

打开网页后，先点击“Accept License Agreement”。  根据操作系统选择相应的版本。

<br/>
 
<center>
###Java JDK8 在 Windows 10 下的安装以及环境变量的配置
</center>
                   
在Windows 中，双击安装就是,但是安装好以后可能需要配置环境变量。                       
Win10下JDK8环境变量的配置：                              
依次单击计算机（Computer），选择属性（Properties）,选择高级系统设置（Advanced systems settings）, 选择环境变量（Environment  Variables）.            
新建3个环境变量（PATH，CLASSPATH, JAVA_HOME），若有则不用新建。                         
给3个环境变量增加相应的值（由Java所在的路径决定，根据具体情况修改），例如：  

         PATH    D:\Program Files\Java\jdk1.8.0_10\bin;  D:\Program  Files\Java\jdk1.8.0_10\jre\bin                      
         CLASSPATH   D:\Program  Files\Java\jdk1.8.0_10\lib;  D:\Program  Files\Java\jdk1.8.0_10\lib\tools.jar           
         JAVA_HOME    D:\Program  Files\Java\jdk1.8.0_10                            

不同路径之间用分号隔开。                                 

若添加正确，注销或重启计算机以后，在PowerShell或cmd中输入`java -version`和`javac -version`会显示版本信息。                  

<br/>

<center>
###Java JDK8 在 Linux 下的安装以及环境变量的配置
</center>

1  下载，根据 Linux系统的位数选择，这里以后缀为.tar.gz的为例，.rpm的直接安装就是。

2  解压。

3  把解压后的文件夹放到/usr/local 下面。（这个随便，任意目录下都可以）

4 在主目录下找到隐藏文件.profile ,  若没有.profile，则去找文件 .bash_profile or .bashrc （注意文件名以点号开头，因为是隐藏文件）。

5 在文件.profile 或 .bash_profile 或 .bashrc 中添加环境变量，在文件的最末尾加上以下4行(需根据具体情况修改，由JAVA所在目录决定)：

    export  JAVA_HOME = /usr/local/jdk1.8.0_10           
    export  JRE_HOME = ${JAVA_HOME}/jre          
    export  CLASSPATH = .:${JAVA_HOME}/lib:${JRE_HOME}/lib            
    export  PATH = ${JAVA_HOME}/bin:$PATH                    


若添加正确，注销或重启计算机以后，在Bash Shell中输入：  

     java  -version           
     javac  -version                      

都会显示版本信息。
                           
