#### Doker安装

```shell
# 自动安装
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```

#### 启动Doker

```shell
systemctl start docker
```

#### 测试Doker

```shell
# 拉取镜像
sudo docker pull hello-world
# 执行hello-world
sudo docker run hello-world
```

```shell
# 成功显示
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

#### Docker与宿主机的文件系统

```shell
# Docker并不与宿主机共享文件系统
# 需要将宿主机的文件挂载到Docker以实现共享
```

#### Docker操作

###### 查看Docker镜像并追加到文件

```shell
# 查看镜像列表
docker images
# 查看Docker镜像并追加到文件
echo -e "\n$(docker images)" >> exam8.txt
```

###### 拉取镜像

```shell
# latest标签代表最新
docker pull ngnix:latest
```

###### 新建并启动容器

```shell
docker run -d --name nginxv1 -p 80:80 -v /root/nginx/html:/usr/share/nginx/html nginx

# - -d:以守护进程模式运行容器,后台运行
# - --name nginxv1:指定容器名称为nginxv1
# - -p 80:80:将容器的80端口映射到宿主机的80端口
# - -v /root/nginx/html:/usr/share/nginx/html:将宿主机/root/nginx/html目录挂载到容器
# 最后为指定镜像名称

其中-v /root/nginx/html:/usr/share/nginx/html会自动创建文件夹
```

###### 查看docker文件夹

```shell
# 进入指定容器(ngnixv1为创建容器时的命名)
docker exec -it nginxv1 /bin/bash
```

###### 创建镜像

```shell
# 先查看容器的CONTAINER ID
docker ps
# docker commit CONTAINER_ID new_images_name:tag
```

###### Dockerfile

```shell
# dockerfile要从FROM开始
# 要避免语法混合,在一行中不能既有命令又有注释。


FROM nginx
# 基础镜像为nginx
MAINTAINER scau202125330220
# 镜像维护者信息 
EXPOSE 80
# 暴露80端口
VOLUME /usr/share/nginx/html/
# 创建挂载点/usr/share/nginx/html
```

###### 使用Dockerfile构建镜像

```shell
# 通过Dockerfile来创建镜像
docker build -t mynginx:v2 .
# -t用于指定目标镜像名称和标签,这里为mynginx:v2
# .代表使用当前目录下的Dockerfile构建
```

