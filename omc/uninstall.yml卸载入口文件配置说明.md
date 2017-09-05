# uninstall.yml卸载入口文件配置说明

卸载应用程序的运维入口脚本是/home/omc-playbook/uninstall.yml，
如果需要设置应用卸载选项，编辑变量文件/home/omc-playbook/group_vars/omc-uninstalls选择需要写卸载的应用。
```
IsUninstallAAA: True
IsUninstallMQ_AD: True
IsUninstallMQ: True
IsUninstalladm: True
IsUninstallADs: True
IsUninstallBO: True
IsUninstallffmpeg: True
IsUninstallMysql: True
IsUninstallNginx: True
IsUninstallPortal: True
IsUninstallPush: True
IsUninstallUAS: True
IsUninstallUBA: True
IsUninstallVsftpd: True
is_keepalived_uninstall: True
is_denyhosts_uninstall: True
is_nagios_server_uninstall: True
is_nagios_client_uninstall: True
```

* 配置文件中True代表确认卸载，如果不需卸载则将True改为False即可。


卸载需要执行下面命令
```
ansible-playbook -i /home/omc-playbook/production  /home/omc-playbook/ uninstall.yml
```