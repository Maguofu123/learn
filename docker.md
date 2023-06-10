# docker
## day1
> 隔离机制
- 镜像（image）：模板，创建容器服务
- 容器（container）：独立运行或一组应用
- 仓库（repository）：存放镜像的地方，分为公有仓库和私有仓库，国外仓库和国内仓库（通过镜像加速）

配置阿里云镜像

> 命令
- `docker run 文件` 
- `docker --help`

> 镜像命令
- `docker images` 加载所有镜像
- `docker pull` 拉取镜像
- `docker rmi -f id或者名字`
- `docker rmi -f $(docker images -aq)` 递归删除，即删除所有容器

> 容器命令
- `docker run 容器id`
- `docker ps [-a]` 显示当前运行的容器
- `ctrl + p + q` 退出但不停止运行
- `docker rm 容器id`
- `docker rm -a -q|xargs docker rm` 删除所有容器

> 启动和停止容器
- `docker start`
- `docker restart`
- `docker stop`
- `docker kill`

> 其他命令
- `docker run -d` 后台运行
- `docker logs -tf --tail 10 id` 查看日志
- `docker top 容器id` 查看镜像

> 进入容器
- `docker exec id`  进入容器后开启新的终端
- `docker attach id` 进入容器正在执行的终端

> 拷贝
- `docker cp`

## day2
部署Nginx
- 端口暴露 -p 外部公网端口：容器内部端口
- `docker run -d --name nginx01 -p:3344:80 nginx` 

安装tomcat
- `docker run -it --rm tomcat:9.0` 下载并运行容器，退出后删除容器，镜像还在

外部映射

es+kibana

可视化 portainer

commit镜像
`docker commit -a="ma98"（提交者名字） -m="add webapps app"（描述） e987c0f700fc tomcat02（名字）:1.0（版本号）`

**容器数据卷** 容器持久化和同步操作
- 使用命令挂载`-v` `docker run -it -v 主机目录：容器内目录 -p ` 
- `-v`挂载，`-e`设置环境

具名和匿名挂载 ro，rw改变读写权限
- 具名挂载 `-v 卷名：容器内路径` 方便找到卷
- 匿名挂载 `-v 容器内路径`
- 指定路径挂载 `-v /宿主机路径：容器内路径`  

**dockerFile**
`docker build -f /home/docker-test-volume/dockerfile1 -t kuangshen/centos:1.0 .`
1. 编写dockerfile文件
2. docker build构建一个镜像
3. docker run运行镜像
4. docker push发布镜像

> dockerFile命令
- `FROM 基础镜像`
- `MAINTAINER 姓名+邮箱`
- `RUN 需要运行的命令`
- `ADD 添加内容`
- `WORKDIR 镜像工作目录`
- `VOLUME 挂载目录`
- `EXPOSE 暴露端口配置`
- `CMD 容器启动时执行的命令`
- `ENTRYPOINT 容器启动时执行的命令，可以追加命令`
- `ONBUILD `构建继承镜像时执行此命令
- `COPY` 文件拷贝到镜像中
- `ENV` 构建时候设置环境变量


> docker 网络

## day3
![image](https://user-images.githubusercontent.com/91414286/232716833-b7aec445-52c1-4cbb-a272-0e56835322a7.png)


## day4 
网络模式：
- bridge 桥接
- none 不配置网络
- host 和宿主机共享网络
- container 容器网络连通

自定义网络：
`docker network create --driver bridge --subnet 192.168.0.0/16 --gateway 192.168.0.1 mynet`
- 保证集群健康

网络联通：
- `docker network connect` 一个容器，两个ip地址

**springBoot微服务打包docker镜像**
1. 构建springboot项目
2. 打包应用
3. 编写dockerfile
4. 构建镜像
5. 发布运行