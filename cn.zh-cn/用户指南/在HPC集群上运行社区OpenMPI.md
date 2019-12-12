# 在HPC集群上运行社区OpenMPI<a name="ZH-CN_TOPIC_0063506960"></a>

## 操作场景<a name="section36657735152023"></a>

该任务指导用户在已配置好的弹性云服务器上，运行社区MPI应用（3.1.1版本）。

## 前提条件<a name="section9743727152034"></a>

-   已成功创建带IB网卡的弹性云服务器，并绑定了弹性IP进行登录。
-   已使用私有镜像创建多个弹性云服务器。

## 操作步骤<a name="section2553429515210"></a>

1.  使用“PuTTY”，采用密钥对方式登录弹性云服务器。

    登录用户为创建弹性云服务器时指定的用户名。

2.  执行以下命令，防止系统超时退出。

    **\# TMOUT=0**

3.  执行以下命令，验证参加测试的弹性云服务器之间是否可以免密码互相登录。

    $  **ssh** _**用户名**_**@**_**SERVER\_IP**_

4.  执行以下命令，关闭弹性云服务器的防火墙。

    **\# iptables -F**

    **\# service firewalld stop**

5.  执行以下命令，给参与测试的弹性云服务器配置主机名。

    **\# hostnamectl set-hostname vm1**

6.  执行以下命令，添加“/etc/hosts“文件。

    **\# vi /etc/hosts**

    添加的内容为弹性云服务器的主机名及IP地址，例如

    **\#cat /etc/hosts**

    **192.168.1.3 vm1**

    **192.168.1.4 vm2**

    **...**

7.  执行以下命令，添加hostfile文件。

    **\# vi hostfile**

    添加的内容为集群中参与测试的弹性云服务器的主机名。

    **vm1**

    **vm2**

    **...**

8.  修改hostfile，运行MPI benchmark，运行时指定hostfile文件路径。

    以两个弹性云服务器为例：

    **\# mpirun --allow-run-as-root -np 2 --pernode -hostfile /root/hostfile /usr/mpi/gcc/openmpi-3.0.0rc6/tests/imb/IMB-MPI1 PingPong**

    在两个节点的集群间运行Intel MPI benchmark，在RDMA网络下，最低时延应该在1.5 us（microseconds）以内：

    ```
    #------------------------------------------------------------
    #    Intel (R) MPI Benchmarks 4.1, MPI-1 part
    #------------------------------------------------------------
    # Date                  : Mon Jul 16 09:42:15 2018
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
    0         1000         1.75         0.00
    1         1000         1.75         0.55
    2         1000         1.74         1.10
    4         1000         1.74         2.19
    8         1000         1.77         4.31
    16         1000         1.79         8.54
    32         1000         1.77        17.26
    64         1000         1.85        33.02
    128         1000         1.89        64.45
    256         1000         2.39       102.29
    512         1000         2.54       192.56
    1024         1000         2.81       346.99
    2048         1000         3.24       603.08
    4096         1000         4.30       907.66
    8192         1000         5.91      1321.23
    16384         1000         8.61      1814.29
    32768         1000        12.31      2537.83
    65536          640        21.80      2867.15
    131072          320        33.91      3686.23
    262144          160        42.65      5861.95
    524288           80        68.61      7287.12
    1048576           40       120.06      8329.50
    2097152           20       221.55      9027.12
    4194304           10       424.35      9426.16
    
    
    # All processes entering MPI_Finalize
    ```

9.  在Linux集群上部署您自己的MPI 应用，并参考上述MPI运行方法，在Linux 集群中运行MPI 程序。

