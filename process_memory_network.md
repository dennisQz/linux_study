**linux 系统相关（进程，内存，负载，网络）**


###### 1, 使用htop 或 top 监控进程信息
``htop ``   
``top``

###### 2，查看ip    
```方式一： ifconfig```  
```方式二： ip addr```

###### 3，查看nginx进程
ps -ef | grep nginx  // 或者 ps -aux | grep php
root      19989  15286  0 12:24 pts/0    00:00:00 grep --color=auto nginx


>  待了解  
```
进程的查看 -ps命令  和 -pstree命令  和 -top命令
判断服务器健康状态
查看系统所有进程
杀死进程
修改进程的优先级
```  

###### 4, 系统运行时长，负载量
```
uptime
23:01:52 up 1 day,  4:31,  2 users,  load average: 0.00, 0.01, 0.05   
( up 1 day,  4:31 表示已运行1天4小时31分钟； 2个用户连接系统； 过去1, 5, 15 分钟的平均负载量。负载量越低意味着你的系统性能越好)
```

###### 5, 系统虚拟内存使用情况
```free```

###### 6, 关于进程、内存、内存分页、堵塞IO、traps及CPU活动的信息
```
vmstat
vmstat  2  # 每两秒输出一次
vmstat  2 5 # 每两秒输出一次( 共输出五次)
r  b   swpd   free          buff   cache     si   so   bi    bo   in     cs     us  sy  id    wa  st
3  0      0     3175648   3688 428048  0    0     3     3    103  166   0    0  100  0    0

r: 运行队列中进程数量
b: 等待IO的进程数量
Memory（内存）：
swpd: 使用虚拟内存大小
free: 可用内存大小
buff: 用作缓冲的内存大小
cache: 用作缓存的内存大小
Swap：
si: 每秒从交换区写到内存的大小
so: 每秒写入交换区的内存大小
IO：（现在的Linux版本块的大小为1024bytes）
bi: 每秒读取的块数
bo: 每秒写入的块数
```

###### 7, CPU活动的信息
```
top -bn 1 -i -c
top - 17:40:07 up 8 days, 23:09,  4 users,  load average: 0.41, 0.30, 0.16
Tasks: 122 total,   1 running, 121 sleeping,   0 stopped,   0 zombie
%Cpu(s):  15.2 us,  6.7 sy,  0.0 ni, 87.5 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3861480 total,  1261716 free,  1561488 used,  1038276 buff/cache
KiB Swap:  2097148 total,  2097148 free,        0 used.  1765152 avail Mem
// 说明
%15.2 us：表示用户空间程序的cpu使用率（没有通过nice调度）
%6.7 sy：表示系统空间的cpu使用率，主要是内核程序。
%0.0 ni：表示用户空间且通过nice调度过的程序的cpu使用率。
% 87.5 id：空闲cpu
%wa：cpu运行时在等待io的时间
%hi：cpu处理硬中断的数量
%si：cpu处理软中断的数量
%st：被虚拟机偷走的cpu
```


>  netstat 使用
```
1, 根据进程查看端口
netstat -nap | grep 19989
2, 查看8081号端口对应的进程名命令：
netstat -nap | grep 8081
结果：
tcp     0    0 0.0.0.0:8081         0.0.0.0:*         LISTEN      9836/nginx 
3, 显示全部互联网（端口80）连接数量:  
 netstat -an |grep :80 |wc -l  
4, 显示机器上监听的所有端口:  
netstat -ant | grep LISTEN  
5, 在你的LAN上面用nmap命令扫描一个机器，并且获悉它的哪些端口是开放的:  
nmap ip  
```
