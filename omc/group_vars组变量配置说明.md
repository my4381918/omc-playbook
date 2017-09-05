通过变量来决定服务器中应用的配置文件中的配置值，默认采用一组主机使用相同的变量，变量定义在/home/omc-playbook/group_vars目录中。

group_vars下面包含文件all、以主机组命令的文件（二级主机组名称是冒号前面的部分）。

all文件中变量作用于所有主机，其他文件变量是能在固定的主机组中可用。

```
# file : group_var/all
#db passwd
rootPasswd: root
#choice to install(True/False)
IsInstallBO: True
IsInstallPortal: True
IsInstallAAA: True
IsInstallPush: True
IsInstallUBA: True
IsInstallAD: True
IsInstallDenyHosts: True

#ulimit参数(默认，一遍不需修改)
soft_nofile_number: 102400
hard_nofile_number: 102400

# Here are variables for nagios server install
# 修改nagios报警的联系人和联系方式（邮箱）
contact_name1: zhouguangcan
contact_name2: zhangyifei
contact_name3: qiaowenwei
contact_name1_email: zhouguangcan123@sumaott.com
contact_name2_email: zhangyifei123@sumaott.com
contact_name3_email: qiaowenwei123@sumaott.com
# nagios管理页面的账号密码
nagiosadmin: nagios
nagiospassword: sumavision
# nagios 主机组定义，按下述模板编辑
host_group:
  bo_group:
    bo1: "192.166.62.100"
    bo2: "192.166.62.101"
  portal_group:
    portal1: "192.166.62.102"
    portal2: "192.166.62.103"

# Here are variables for nagios client install
# nagios监控项的参数
nagios_server_ip: 192.166.62.103
ntp_server_ip: 192.166.62.103
check_net_device: bond1
check_disk_partition: sda1
dbuser: root
dbpassword: sumavision

#nginx负载均衡代理的端口
Portal_port: 9080
AAA_port: 9080
PIC_port: 9082
```
其他组变量需根据自己的需要定义，比如要安装keepalive，需修改group_vars/keepalivedmaster1
```
---
#file: group_vars/keepalivedmaster
virtual_state: MASTER
keepalived_ip: 192.166.62.100
keepalived_device: eth0
vvid: 100
priority: 100
virtual_ip: 192.166.62.104
```
然后修改group_vars/keepalivedslave1

```
---
#file: group_vars/keepalivedmaster
virtual_state: SLAVE
keepalived_ip: 192.166.62.101
keepalived_device: eth0
vvid: 100
priority: 70
virtual_ip: 192.166.62.104
```

要保证安装后功能正常，必须明确每一个参数的意义并正确配置。