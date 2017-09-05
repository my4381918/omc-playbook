# production主机变量配置说明

主机信息的配置文件是/home/omc-playbook/production，文件内容如下：
```
# file production
[omc-dbservers]
192.166.62.100

[mq-servers]
192.166.62.100
192.166.62.101

[dbservers:children]
omc-dbservers

[mqservers:children]
mq-servers

[omc-picservers]
192.166.62.100
192.166.62.101

[picservers:children]
omc-picservers

[omc-boservers]
192.166.62.100

[boservers:children]
omc-boservers

[omc-portalservers1]
192.166.62.102

[omc-portalservers2]
192.166.62.103

[portalservers:children]
omc-portalservers1
omc-portalservers2

[omc-aaaservers]
192.166.62.102
192.166.62.103

[aaaservers:children]
omc-aaaservers

[omc-ubaservers]
192.166.62.100
192.166.62.101

[ubaservers:children]
omc-ubaservers

[omc-pushservers]
192.166.62.102
192.166.62.103

[pushservers:children]
omc-pushservers

[omc-adservers]
192.166.62.100

[adservers:children]
omc-adservers

[omc-ntp-server]
192.166.62.103

[ntpserver:children]
omc-ntp-server

[omc-ntp-clients]
192.166.62.100
192.166.62.101
192.166.62.102

[ntpclients:children]
omc-ntp-clients

[omc-loadbalancese]
192.166.62.102
192.166.62.103

[loadbalanceservers:children]
omc-loadbalancese

[omc-mysql_1]                # mysql主主复制，固定主机组
192.166.62.100

[omc-mysql_2]                # mysql主主复制，固定主机组
192.166.62.101

[mysqlReplication:children]
omc-mysql_1
omc-mysql_2

[omc-uninstalls]
192.166.62.100
192.166.62.101
192.166.62.102
192.166.62.103

[uninstalls:children]
omc-uninstalls

[keepalivedmaster1]
192.166.62.100

[keepalivedmaster2]
192.166.62.102


[keepalivedmaster:children]
keepalivedmaster1
keepalivedmaster2

[keepalivedslave1]
192.166.62.101

[keepalivedslave2]
192.166.62.103

[keepalivedslave:children]
keepalivedslave1
keepalivedslave2

[nserver]
192.166.62.103
[nclient]
192.166.62.100
192.166.62.101
192.166.62.102
```

表中采用最多两层的方式，定义了主机，主机组和二层主机组。主机信息推荐直接添加Ip地址，主机组和二层主机组中有一些固定组名是和操作已经绑定，信息如下：

role | 说明
---|---
[dbservers:children] |	数据库安装和建表操作
[mqservers:children] |	Active-mq主机组
[picservers:children] |	图片服务器的主机组
[boservers:children] |	BO服务器主机组
[portalservers:children]	| Portal服务器主机组
[aaaservers:children] |	AAA服务器主机组
[ubaservers:children] |	UBA服务器主机组
[pushservers:children] |	Push服务器主机组
[adservers:children] |	广告服务器主机组
[ntpserver:children] |	本地时间服务器组
[ntpclients:children] |	本地需要设置时间同步的主机组
[loadbalanceservers:children] |	Nginx负载均衡安装主机组
[mysqlReplication:children] |	Mysql主主复制主机组
[uninstalls:children] |	卸载操作进行的主机组
[keepalivedmaster:children] |	Keeplived的master主机组
[keepalivedslave:children] |	Keeplived的slave主机组 |
[nserver] |	安装nagios server的主机组
[nclient] |	安装nagios client的主机组

二级分组的作用：对整组服务器采用相同安装操作，对相同子组的服务器使用相同的变量。变量主要决定服务器中配置文件中的配置项目的值。