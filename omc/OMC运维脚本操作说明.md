# 安装OMC运维脚本
将安装包里的omc-playbook_V2.0.tar.gz上传至ansible主机home目录下并解压,
```
cd /home
tar -zxvf omc-playbook_V2.0.tar.gz
```

# 编辑配置文件
运维人员需要编辑omc-playbook下的以下文件：
```
* production        #定义主机
* site.yml/update.yml/rollback.yml/uninstall.yml          #确认安装/升级/回滚/卸载的模块，按需编辑
* group_var/all     #全局变量文件
* group_vars/*      #主机组变量文件，编辑所需模块相关的变量
```

# 运行
### 部署时执行
```
ansible-playbook -i /home/omc-playbook/production  /home/omc-playbook/site.yml
```
### 升级时执行
```
ansible-playbook -i /home/omc-playbook/production  /home/omc-playbook/update.yml
```
### 回滚时执行
```
ansible-playbook -i /home/omc-playbook/production  /home/omc-playbook/rollback.yml
```
### 卸载时执行
```
ansible-playbook -i /home/omc-playbook/production  /home/omc-playbook/uninstall.yml
```