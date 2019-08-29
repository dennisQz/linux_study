__linux下文件或文件夹操作__

###### 创建或打开文件  
``vi filename``
###### 创建文件夹  
``mkdir folderName``

###### 撤销&取消撤销  
``撤销： 先按ESC 再按u键，相当于windows 下的ctrl+z``  
``取消撤销： 先按ESC  再按ctrl+r``

###### 复制粘贴快捷键
``复制: ctrl + insert 键`` 
``粘贴：shift + insert 键``

###### Linux 删除文件夹和文件的命令  
直接rm就可以了，不过要加两个参数-rf 即：  
``rm -rf 目录名字``  
-r 就是向下递归，子级目录及文件一并删除  
-f 就是直接强行删除- force  

* 1，删除文件夹实例：
rm -rf /var/log/httpd/access
将会删除/var/log/httpd/access目录以及其下所有文件、文件夹

* 2，删除文件使用实例：
rm -f /var/log/httpd/access.log
将会强制删除/var/log/httpd/access.log这个文件

* 3，vi\vim 清空文件内容快捷命令
在命令模式下，首先执行  gg ，这里是跳至文件首行，再执行：dG ，这样就清空了整个文件！

* 4，删除特殊文件名文件：
rm -rf  ./"\opt\project\hby"*
删除文件名为 【\opt\project\hby】的文件

* 5，删除某个文件夹下30天前的文件
find /logs -type f -ctime +30 | xargs rm -rf （删除30天之前文件的命令）

###### Linux 重命名文件及文件夹  
mv命令实际应用中，只能对单个文件重命名，命令如下：  
``mv [path/]oldfilename [path/]newfilename``

**rename**命令专用于文件重命名，rename除了给单个文件重命名，还可以批量文件重命名
rename命令带3个参数,命令如下：
``rename foo foo0 foo*`` 
则从foo0200到foo0278的所有文件都被重命名为foo200到foo278，文件名中的foo0被替换为foo。

###### Linux 拷贝文件夹和文件的命令  
:参考http://www.cnblogs.com/xd502djj/archive/2011/11/25/2263562.html  
同级目录 
``cp -rf js js.bak``  
不同级目录  
远程拷贝-从一台服务器拷贝到另一台服务器  
``scp -r /opt/project/crm-v2/template root@192.168.2.181:/opt/project/crm-v4/ ``  
将crm-v2下template目录拷贝到 远程crm-v4目录下面（完成后v4目录下多出template目录）
强制拷贝不提示”是否覆盖“( 将_new  目录拷贝到 debug目录下)
``\cp -rf /opt/rsync/uatpre/uatcrm/svn-uat-crm/public/debug/_new  /opt/rsync/crmpre/public/debug``

###### vi 文件内跳转
```
1，大写G跳到最后一行
2，按两次'g'跳转到第一行
```
###### vi 编辑文件  
键入【i】进入编辑模式：  
```
Esc 状态下：
:wq 保存并退出
:q! 不保存退出
:x 保存退出
```
