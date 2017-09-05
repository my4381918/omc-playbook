# rollback.yml回滚入口文件配置说明

回滚对应更新操作，回滚应用程序的运维入口脚本是/home/omc-playbook/rollba
ck.yml，文件内容如下：
（如果不需要安装的部分，可以#注释掉相关调用）
```
- include: rollback_dbservers.yml
- include: rollback_aaaservers.yml
- include: rollback_adservers_adm.yml
- include: rollback_adservers_cpm.yml
- include: rollback_adservers_uas.yml
- include: rollback_boservers.yml
- include: rollback_portalservers_msg.yml
- include: rollback_portalservers.yml
- include: rollback_pushservers.yml
- include: rollback_ubaservers.yml
```

注意如果想使用回滚数据，需要保证数据升级操作是可以回滚的，并且将研发提供的回滚数据库的脚本放到/home/omc-playbook/roles/rollback_mysql/files目录中，替换对应的文件

回滚需要执行下面命令
```
ansible-playbook -i /home/omc-playbook/production  /home/omc-playbook/rollabck.yml
```