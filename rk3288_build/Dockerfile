# 制作镜像命令：
# 1、将本文件复制至/home/make-docker-images,文件名必须为Dockerfile
# 2、cd /home/make-docker-images
# 3、编译进行命令：docker build -t rk3288_linux ./
# 4、删除镜像命令：docker rmi + imageid
# 5. docker run -it ubuntu /bin/bash
# 6.  docker run -it  -v /home/zwf:/home/ky --name rk3288 rk3288_linux 映射本地目录到docker
# 基础镜像：ubuntu1:18.04
FROM ubuntu:18.04
MAINTAINER zwf "zwf@kuaiyu.com"
RUN  sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN  apt-get clean
RUN  apt-get update

# 设置中文编码
ENV LANG C.UTF-8
#定义时区参数
RUN apt-get install -y \
    vim net-tools sudo gawk \
    tar git curl wget build-essential u-boot-tools cpio busybox \
	libncurses5-dev lib32ncurses5 lib32z1 lib32stdc++6
COPY ./files/localtime /etc/localtime
RUN apt-get install -y repo git ssh make gcc libssl-dev liblz4-tool \
	expect g++ patchelf chrpath gawk texinfo chrpath diffstat binfmt-support \
	qemu-user-static live-build bison flex fakeroot cmake gcc-multilib g++-multilib unzip \
	device-tree-compiler python-pip ncurses-dev bc time rsync
RUN useradd --create-home --no-log-init --shell /bin/bash ky
RUN adduser ky sudo
RUN echo 'root:1' | chpasswd
RUN echo 'ky:1' | chpasswd
USER ky
WORKDIR /home/ky
