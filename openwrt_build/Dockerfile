# 制作镜像命令：
# 1、将本文件复制至/home/make-docker-images,文件名必须为Dockerfile
# 2、cd /home/make-docker-images
# 3、编译进行命令：docker build -t openwrt ./
# 4、删除镜像命令：docker rmi + imageid
# 5. docker run -it ubuntu /bin/bash
# 6.  docker run -it  -v /home/zwf:/home/ky --name test1 test 映射本地目录到docker
# 基础镜像：ubuntu1:20.04

FROM ubuntu:20.04

RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN  apt-get clean
RUN  apt-get update
COPY ./files/localtime /etc/localtime

# 设置中文编码
ENV LANG C.UTF-8
#
RUN apt-get install -y sudo time git-core subversion build-essential gcc-multilib \
                       g++-multilib libncurses5-dev zlib1g-dev gawk flex gettext wget unzip python3 rsync &&\
    apt-get clean

RUN useradd -m openwrt &&\
    echo 'openwrt ALL=NOPASSWD: ALL' > /etc/sudoers.d/openwrt

USER openwrt
WORKDIR /home/openwrt
