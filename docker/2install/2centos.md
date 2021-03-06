## CentOS 安装 Docker CE {#centos-安装-docker-ce}

### 准备工作 {#准备工作}

#### 系统要求 {#系统要求}

Docker CE 支持 64 位版本 CentOS 7，并且要求内核版本不低于 3.10。 CentOS 7 满足最低内核的要求，但由于内核版本比较低，部分功能（如`overlay2`存储层驱动）无法使用，并且部分功能可能不太稳定。

#### 卸载旧版本 {#卸载旧版本}

旧版本的 Docker 称为`docker`或者`docker-engine`，使用以下命令卸载旧版本：

```
# yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
```

### 使用 yum 安装 {#使用-yum-安装}

执行以下命令安装依赖包：

```
# yum install -y yum-utils device-mapper-persistent-data lvm2
```

鉴于国内网络问题，强烈建议使用国内源，这里使用阿里云的yum源。

执行下面的命令添加`yum`软件源：

```
# yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

更新 yum 缓存：

```
# yum makecache fast
```

#### 安装 Docker CE {#安装-docker-ce}

```
# yum -y install docker-ce
```

### 使用脚本自动安装 {#使用脚本自动安装}

在测试或开发环境中 Docker 官方为了简化安装流程，提供了一套便捷的安装脚本，CentOS 系统上可以使用这套脚本安装：

```
# curl -fsSL get.docker.com -o get-docker.sh
# sh get-docker.sh --mirror Aliyun
```

执行这个命令后，脚本就会自动的将一切准备工作做好，并且把 Docker CE 的 Edge 版本安装在系统中。

### 启动 Docker CE {#启动-docker-ce}

```
# systemctl daemon-reload
# systemctl enable docker
# systemctl start docker
```

### 建立 docker 用户组 {#建立-docker-用户组}

默认情况下，`docker`命令会使用[Unix socket](https://en.wikipedia.org/wiki/Unix_domain_socket)与 Docker 引擎通讯。而只有`root`用户和`docker`组的用户才可以访问 Docker 引擎的 Unix socket。出于安全考虑，一般 Linux 系统上不会直接使用`root`用户。因此，更好地做法是将需要使用`docker`的用户加入`docker`用户组。

建立`docker`组：

```
# groupadd docker
```

将当前用户加入`docker`组：

```
# usermod -a G docker $USER
```

退出当前终端并重新登录，进行如下测试。

### 测试 Docker 是否安装正确 {#测试-docker-是否安装正确}

```
# docker run hello-world

Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete
Digest: sha256:2557e3c07ed1e38f26e389462d03ed943586f744621577a99efb77324b0fe535
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

若能正常输出以上信息，则说明安装成功。

### 添加内核参数 {#添加内核参数}

默认配置下，如果在 CentOS 使用 Docker CE 看到下面的这些警告信息：

```
WARNING: bridge-nf-call-iptables is disabled
WARNING: bridge-nf-call-ip6tables is disabled
```

请添加内核配置参数以启用这些功能。

```
# tee -a /etc/sysctl.conf <<-EOF
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
```

然后重新加载`sysctl.conf`即可

```
# sysctl -p
```

### 镜像加速 {#参考文档}

参考：[http://www.dockerk8s.net/docker/3image/2image-add-speed.html](http://www.dockerk8s.net/docker/3image/2image-add-speed.html)

### 参考文档 {#参考文档}

* [Docker 官方 CentOS 安装文档](https://docs.docker.com/install/linux/docker-ce/centos/)



