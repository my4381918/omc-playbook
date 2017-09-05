# 建立主机信任
### 单台主机
首先ansible服务端需生成秘钥
执行:
```
ssh-keygen -t rsa -P ''
```
-P '' 就表示空密码，一次回车后，在root目录下生成.ssh目录，.ssh下有id_rsa和id_rsa.pub。

将秘钥添加到客户端：
```
ssh-copy-id -i /root/.ssh/id_rsa.pub {{ipaddr}}

```

### 多台主机
解压附件，附件为python和shell两个脚本。
按照ip：passwd的规则填写配置文件hostsname.txt或者config.json，然后执行脚本：
```
sh test.sh
或者
python setsshlogin.py
```

### 测试
通过 ssh {{ ipaddr }} 测试主机连通性，如果不需输入密码完成登录即正常。

