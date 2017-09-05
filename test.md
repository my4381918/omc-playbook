# 测试主机联通性
编辑ansible配置文件:
```
vim /etc/ansible/hosts
```
新增主机列表，例如：
```
[test]
192.166.62.100
192.166.62.101
192.166.62.102
192.166.62.103
```

执行ansible test -m ping:

如果没有报错，连接success即为成功。


![image](http://image.rifestone.com:8082/upload/qww.png)


