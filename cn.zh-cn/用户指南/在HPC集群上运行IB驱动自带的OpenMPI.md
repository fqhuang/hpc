# 在HPC集群上运行IB驱动自带的OpenMPI<a name="ZH-CN_TOPIC_0062552872"></a>

## 操作场景<a name="section3916646518458"></a>

该任务指导用户在已配置好的弹性云服务器上，运行IB驱动自带的MPI应用（3.0.0rc6版本）。

## 前提条件<a name="section1134164518458"></a>

-   已成功创建带IB网卡的弹性云服务器，并绑定了弹性IP进行登录。
-   已使用私有镜像创建多个弹性云服务器。

## 操作步骤<a name="section3258284118458"></a>

1.  使用“PuTTY”，采用密钥对方式登录弹性云服务器。

    登录用户为创建弹性云服务器时指定的用户名。

2.  执行以下命令，防止系统超时退出。

    **\# TMOUT=0**

3.  执行以下命令，验证参加测试的弹性云服务器之间是否可以免密码互相登录。

    $  **ssh** _**用户名**_**@**_**SERVER\_IP**_

4.  执行以下命令，关闭弹性云服务器的防火墙。

    **\# iptables -F**

    **\# service firewalld stop**

5.  执行以下命令，退出root权限。

    **\# exit**

6.  执行以下命令，添加hostfile文件。

    **\# vi hostfile**

    添加的内容为弹性云服务器的IP地址或者主机名（主机名需要在/etc/hosts中有对应IP地址信息），例如

    **\# cat hostfile**

    **192.168.0.1**

    **192.168.0.2**

    **...**

7.  执行以下命令，在集群中运行hostname命令。

    **\# mpirun --allow-run-as-root -np <hostfile\_node\_number\> -pernode --hostfile hostfile  hostname**

    **图 1**  在集群中运行hostname命令<a name="fig10127531114013"></a>  
    ![](figures/在集群中运行hostname命令.png "在集群中运行hostname命令")

8.  修改hostfile，运行MPI benchmark，运行时指定hostfile文件路径。

    以两个弹性云服务器为例：

    **\# mpirun --allow-run-as-root -np 2 -pernode --hostfile /root/hostfile  /usr/mpi/gcc/openmpi-3.0.0rc6/tests/imb/IMB-MPI1 PingPong**

    在两个节点的集群间运行Intel MPI benchmark，在RDMA网络下，最低时延应该在1.5 us（microseconds）以内：

    ```
    #------------------------------------------------------------
    #    Intel (R) MPI Benchmarks 4.1, MPI-1 part
    #------------------------------------------------------------
    # Date                  : Mon Jul 16 10:12:51 2018
    # Machine               : x86_64
    # System                : Linux
    # Release               : 3.10.0-514.10.2.el7.x86_64
    # Version               : #1 SMP Fri Mar 3 00:04:05 UTC 2017
    # MPI Version           : 3.1
    # MPI Thread Environment:
    
    # New default behavior from Version 3.2 on:
    
    # the number of iterations per message size is cut down
    # dynamically when a certain run time (per message size sample)
    # is expected to be exceeded. Time limit is defined by variable
    # "SECS_PER_SAMPLE" (=> IMB_settings.h)
    # or through the flag => -time
    
    # Calling sequence was:
    
    # /usr/mpi/gcc/openmpi-3.0.0rc6/tests/imb/IMB-MPI1 PingPong
    
    # Minimum message length in bytes:   0
    # Maximum message length in bytes:   4194304
    #
    # MPI_Datatype                   :   MPI_BYTE
    # MPI_Datatype for reductions    :   MPI_FLOAT
    # MPI_Op                         :   MPI_SUM
    #
    #
    
    # List of Benchmarks to run:
    
    # PingPong
    
    #---------------------------------------------------
    # Benchmarking PingPong
    # #processes = 2
    #---------------------------------------------------
    #bytes #repetitions      t[usec]   Mbytes/sec
    0         1000         1.87         0.00
    1         1000         1.93         0.49
    2         1000         1.78         1.07
    4         1000         1.79         2.13
    8         1000         1.77         4.31
    16         1000         1.78         8.57
    32         1000         1.79        17.09
    64         1000         1.85        33.02
    128         1000         1.90        64.12
    256         1000         2.40       101.58
    512         1000         2.53       192.90
    1024         1000         2.85       342.61
    2048         1000         3.23       604.14
    4096         1000         4.32       904.98
    8192         1000         5.89      1325.65
    16384         1000         8.48      1842.47
    32768         1000        12.50      2500.57
    65536          640        21.79      2867.89
    131072          320        34.28      3646.50
    262144          160        42.19      5925.52
    524288           80        66.55      7513.14
    1048576           40       114.95      8699.54
    2097152           20       213.71      9358.48
    4194304           10       402.59      9935.78
    
    
    # All processes entering MPI_Finalize
    ```

9.  在Linux集群上部署您自己的MPI应用，并参考上述MPI运行方法，在Linux集群中运行MPI程序。

