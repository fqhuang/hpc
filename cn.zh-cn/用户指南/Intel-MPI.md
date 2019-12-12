# Intel MPI<a name="ZH-CN_TOPIC_0078129485"></a>

## 操作场景<a name="section37559482203017"></a>

本节指导用户在ECS上安装和使用Intel MPI应用（以版本l\_mpi\_2018.0.128为例）。

## 前提条件<a name="section47764941203023"></a>

已配置弹性云服务器免密登录。

## 操作步骤<a name="section41682873203028"></a>

1.  安装Intel MPI。
    1.  下载Intel MPI。

        下载地址：[https://software.intel.com/en-us/intel-mpi-library](https://software.intel.com/en-us/intel-mpi-library)

    2.  执行以下命令，解压并安装Intel MPI。

        以l\_mpi\_2018.0.128.tgz为例：

        **\# tar -xvf l\_mpi\_2018.0.128.tgz**

        **\# cd l\_mpi\_2018.0.128/**

        **\# ./install.sh**

        **图 1**  Intel MPI安装成功<a name="fig38533160203128"></a>  
        ![](figures/Intel-MPI安装成功.png "Intel-MPI安装成功")

2.  配置环境变量。
    1.  普通用户下，在“\~/.bashrc”中添加如下语句：

        **export PATH=$PATH:/opt/intel/impi/2018.0.128/bin64**

        **export LD\_LIBRARY\_PATH=/opt/intel/impi/2018.0.128/lib64**

    2.  执行下列命令，导入环境变量。

        **\# source \~/.bashrc**

3.  执行下列命令，查看是否导入成功。

    **\# which mpirun**

    **图 2**  环境变量导入成功<a name="fig177461046619"></a>  
    ![](figures/环境变量导入成功.png "环境变量导入成功")

    回显结果如[图2](#fig177461046619)所示，表示环境变量导入成功。

4.  执行以下命令，在单个ECS上运行Intel MPI。
    1.  执行以下命令，重新生成可执行文件。

        **\# cd**

        **\# mpicc hello.c -o intel\_hello**

    2.  执行以下命令，在单个ECS上运行Intel MPI。

        **\# mpirun -np 2 /root/intel\_hello**

        **图 3**  在单个ECS上运行Intel MPI<a name="fig1267315562373"></a>  
        ![](figures/在单个ECS上运行Intel-MPI.png "在单个ECS上运行Intel-MPI")



