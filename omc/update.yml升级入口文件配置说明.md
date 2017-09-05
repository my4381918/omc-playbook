# update.yml升级入口文件配置说明

更新应用程序的运维入口脚本是/home/omc-playbook/update.yml，文件内容如下：
（如果不需要安装的部分，可以注释掉相关调用）
```
#- include: update_dbservers.yml                         # 更新数据库
- include: update_aaaservers.yml                         # 更新AAA
- include: update_adservers_adm.yml                     # 更新adm
- include: update_adservers_cpm.yml                     # 更新cpm
- include: update_adservers_uas.yml                      # 更新 uas
- include: update_boservers.yml                          # 更新bo
- include: update_portalservers_smg.yml                   # 更新smg
- include: update_portalservers.yml                         #更新Portal
- include: update_pushservers.yml                          #更新Push
- include: update_ubaservers.yml                           #更新 uba
```
更新包方式说明：以Portal为例，一次完成的更新，需要研发提供PortalServer-App.war，update_portaldb.sql，以及配置文件的模板文件configinfo.properties和jdbc.properties等，别且用准备的文件替换下列的相应文件

```
/home/omc-playbook/roles/update_tomcat-8080-portal/templates/configinfo.properties
/home/omc-playbook/roles/update_tomcat-8080-portal/templates/jdbc.properties
/home/omc-playbook/roles/update_tomcat-8080-portal/files/PortalServer-App.war
/home/omc-playbook/roles/update_mysql/files/update_portaldb.sql
```
更新需要执行下面命令
	
* ansible-playbook -i /home/omc-playbook/production  /home/omc-playbook/update.yml

Ps: 如果只需要单独进行某个安装更新，例如进行Portal不带数据更新，可以单独调用update_portalservers.yml。