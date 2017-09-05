# site.yml入口地址文件配置说明

site.yml是ansible的入口文件，确定了要安装的模块。如果不需要安装该模块可以选择添加#，注释掉。

```
# file site.yml

# system optimize
- include: services.yml                           #设置iptables等基本服务的开关
- include: ulimit.yml                             #优化系统的连接数设置
- include: sysctl.yml                             #优化TCP连接参数
#安装基础软件
- include: ntpserver.yml                          #安装NTP时间服务器
- include: ntpclients.yml                         #设置NTP时间同步
- include: keepalived.yml                         #安装keeplived
- include: loadbalanceservers.yml                 #安装nginx最为负载均衡
- include: mysqlReplication.yml                   #安装两台mysql主主复制
- include: dbservers.yml                          #安装配置mysql建表和导入数据
- include: mqservers.yml                          #安装activeMQ
- include: picservers.yml                         #安装安装图片服务器
#安装安全软件
- include: denyhosts.yml                          #linux安全设置
  when: IsInstallDenyHosts == True

# 安装web服务模块
- include: boservers.yml                          #安装BO服务
  when: IsInstallBO == True

- include: portalservers.yml                      #安装Portal服务
  when: IsInstallPortal == True
  
- include: aaaservers.yml                         #安装AAA服务
  when: IsInstallAAA == True

- include: pushservers.yml                        #安装推送服务
  when: IsInstallPush == True

- include: ubaservers.yml                         #安装uba服务
  when: IsInstallUBA == True

- include: adservers.yml                          #安装ad服务
  when: IsInstallAD == True
# 安装nagios监控
- include: nclient.yml                            #安装nagios被监控端
- include: nserver.yml                            #安装nagios监控服务
```
