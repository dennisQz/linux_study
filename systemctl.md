__centos7下systemctl命令__


###### 启动服务   
``systemctl start postfix.service``

###### 关闭服务  
``systemctl stop postfix.service``

###### 重启服务    
``systemctl restart postfix.service``

###### 显示一个服务的状态  
``systemctl status postfix.service``

###### 在开机时启用一个服务     
``systemctl enable postfix.service``

###### 在开机时禁用一个服务
``systemctl disable postfix.service``

###### 查看服务是否开机启动  
``systemctl is-enabled postfix.service``

###### 查看已启动的服务列表   
``systemctl list-unit-files | grep enabled``

###### 查看启动失败的服务列表      
``systemctl --failed``

###### 列出所有已经安装的`服务`及`状态` （内容简略、清晰）   
```systemctl   list-unit-files```

###### 列出正在运行的服务状态(内容复杂、全面)   
```systemctl``` 
