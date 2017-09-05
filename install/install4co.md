# redhat安装
如果服务器版本是CentOS6.5或者6.8版本，将安装包中ansible4centos.tar.gz上传至服务器/home/soft/目录，执行：
```
tar -zxvf ansible4centos.tar.gz
cd package/
rpm -ivh *
```

如果服务器安装系统时基于软件开发工作站模式安装，则上述安装包可以执行成功。

如果因服务器环境问题导致安装失败，缺少的依赖安装包需自己下载。

