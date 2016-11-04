---
layout: post
title: Linux下BLAST+的本地化
category: Bioinformatics
tags: BLAST   安装配置   
keywords: 
description: 
---
 
<center> 
### Linux下BLAST+的本地化 （NCBI-BLAST 2.5.0+单机运行的方法）
</center> 


本人在以下环境亲测有效：CentOS and Ubuntu Linux 64 Bit.                       
下面涉及到的路径需要根据自己的电脑来修改。


### 1.  下载软件BLAST:
在以下网址  ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/    下载:                           
`ncbi-blast-2.5.0+-x64-linux.tar.gz` （根据自己的操作系统选择）。


### 2.  解压:
解压后放在任意目录下都可以，把相应路径加入PATH变量就是。                                          
比如解压到用户的主目录(/home/yonpen)下，把解压后的文件夹重新命名为blast，则BLAST+的所有程序在目录/home/yonpen/blast/bin下。


###  3.  添加环境变量:
打开终端（Terminal）， 执行:                                        
      vim  ~/.profile                        
      or vim  ~/.bashrc                  

在最末尾添加：             

    export PATH=/home/yonpen/blast/bin:$PATH                           

保存退出。（环境变量的值由Blast所在路径决定。）                      

此处若成功，注销以后执行`blastn -version`会出现版本信息（一定要先注销或重启电脑）。


###  4.  新建:
在目录/home/yonpen/blast下新建一个文件夹，命名为db 。
在/home/yonpen下新建一个文件，命名为.ncbirc 。（文件名是以点号开头的）
在文件中添加内容：

    [BLAST]

    BLASTDB=/home/yonpen/blast/db


###  5. 下载FASTA格式的数据库:
 ftp://ftp.ncbi.nlm.nih.gov/blast/db/FASTA/
如下载nr.gz。


###  6. 建立BLAST+可用的数据库:
打开终端（Terminal），切换到/home/yonpen/blast/db目录下，执行（以蛋白质库nr为例）：                        

      makeblastdb  –in nr  -parse_seqids  -hash_index  -dbtype prot  

(需要自己输入，复制这行命令可能不行，不知道为什么)



###  7.  使用:
如使用psiblast
在目录/home/yonpen/blast下新建3个文件夹，分别命名为pssm,input,output
设待查询序列所在文件的名字为a.fasta（一个文件放一条序列，且必须为fasta格式）
执行命令：
                             
       psiblast  -comp_based_stats 1  -evalue 0.001  -num_iterations 3  -db nr   -query input/a.fasta  -out output/a.txt  -out_ascii_pssm pssm/a.pssm      
                



