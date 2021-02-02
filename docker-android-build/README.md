## 制作镜像命令：
1、将本文件复制至/home/make-docker-images,文件名必须为Dockerfile
2、cd /home/make-docker-images
3、编译进行命令：docker build -t jdk8 ./
## 删除镜像:
1、docker rmi + imageid
## 运行镜像
1、 docker run -it ubuntu /bin/bash
2、 docker run -it  -v /home/zwf:/home/ky --name test1 test 映射本地目录到docker




