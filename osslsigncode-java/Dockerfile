#选择ubuntu为基础镜像
FROM ubuntu:20.04
MAINTAINER wuth <wuth@kinggrid.com>
#修改镜像源为阿里云，按照ubuntu默认的，执行update时会超时报错
RUN sed -i "s/cn.archive.ubuntu.com/mirrors.aliyun.com/g" /etc/apt/sources.list
RUN sed -i "s/security.ubuntu.com/mirrors.aliyun.com/g" /etc/apt/sources.list
RUN sed -i "s/archive.ubuntu.com/mirrors.aliyun.com/g" /etc/apt/sources.list
#更新apt-get
RUN apt-get update -y
RUN apt -y upgrade
# 设置本地语言,可以去掉
ENV LANG en_US.utf8
# 安装相关依赖
RUN apt-get install -y gcc
RUN apt install openssl libssl-dev -y
RUN apt-get install curl -y
RUN apt-get install libcurl4-gnutls-dev -y
RUN apt install build-essential  libssl-dev libcurl4-openssl-dev -y
# 将osslsigncode的源码复制到容器中，并改名
COPY ./osslsigncode-2.1.0.tar.gz /mnt/app.tar.gz
#切换工作目录，对文件进行解压，重命名
WORKDIR /mnt
RUN tar -zxvf app.tar.gz
RUN mv osslsigncode-2.1.0/ ./osslsigncode
#切换到源码目录，执行相关编译
WORKDIR /mnt/osslsigncode
RUN ./configure && make && make install
#添加jdk，并设置环境变量
ADD ./jdk-8u301-linux-x64.tar.gz /usr/local/java/
ENV JAVA_HOME=/usr/local/java/jdk1.8.0_301
ENV CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV PATH=$JAVA_HOME/bin:$PATH
 
