### docker安装并配置阿里镜像加速
#### mac安装
---
* [下载docker for mac](https://download.docker.com/mac/stable/Docker.dmg)

* 右键点击桌面顶栏的 docker 图标，选择 Preferences ，在 Daemon 标签（Docker 17.03 之前版本为 Advanced 标签）下的 Registry mirrors 列表中将 https://5dezk1xb.mirror.aliyuncs.com（每个阿里账号的连接都不同）加到"registry-mirrors"的数组里，点击 Apply & Restart按钮，等待Docker重启并应用配置的镜像加速器。

#### centos 安装
    删除老版本docker 
    sudo yum remove docker \
              docker-client \
              docker-client-latest \
              docker-common \
              docker-latest \
              docker-latest-logrotate \
              docker-logrotate \
              docker-selinux \
              docker-engine-selinux \
              docker-engine
    安装必要的一些系统工具
    sudo yum install -y yum-utils device-mapper-persistent-data lvm2
    添加软件源信息
    sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
    更新并安装 Docker-CE
    sudo yum makecache fast
    sudo yum -y install docker-ce（如果出现 OCI runtime create failed: unable to retrieve OCI runtime error，系统版本和docker版本对不上，安装低版本（sudo yum install docker-ce-17.06.0.ce）或者升级系统(sudo yum update)，建议安装低版本docker）
    开启Docker服务
    sudo service docker start

* 安装参考：https://docs.docker.com/install/linux/docker-ce/centos/#install-docker-ce-1
  
* 安装docker-compose

      sudo yum install python-devel
      sudo yum install libevent-devel
      sudo yum -y install epel-release
      yum install python-pip
      pip install --upgrade pip
      pip install gevent
      pip install docker-compose

* docker-compose安装参考
      https://docs.docker.com/compose/install/#install-compose
      https://www.cnblogs.com/YatHo/p/7815400.html
      https://www.cnblogs.com/gerrydeng/p/7159021.html

* [docker语法学习](https://segmentfault.com/a/1190000010541792)
* [docker-compose语法](https://www.cnblogs.com/freefei/p/5311294.html) \
 [volume-from](http://blog.csdn.net/chancein007/article/details/50645199)

* [常见错误参考](http://note.youdao.com/noteshare?id=361846e8341a810dad065f54331b7f36)

### 启动项目
进入本项目所在的目录运行以下脚本，系统会自动拉取项目的image

      docker-compose up -d
