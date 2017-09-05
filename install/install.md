# 安装ansible
### EPEL源安装方式

如果服务器有外网，直接通过epel源安装
```
rpm -ivh  https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
yum install ansible -y
```
如果服务器没有外网，只能采用安装包方式安装。
