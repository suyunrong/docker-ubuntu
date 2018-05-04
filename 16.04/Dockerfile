FROM ubuntu:16.04
LABEL authors=suyunrong

#================================================
# 配置apt-get源
#================================================
RUN  echo "deb http://archive.ubuntu.com/ubuntu xenial main universe\n" > /etc/apt/sources.list \
  && echo "deb http://archive.ubuntu.com/ubuntu xenial-updates main universe\n" >> /etc/apt/sources.list \
  && echo "deb http://security.ubuntu.com/ubuntu xenial-security main universe\n" >> /etc/apt/sources.list

# No interactive frontend during docker build
ENV DEBIAN_FRONTEND=noninteractive \
    DEBCONF_NONINTERACTIVE_SEEN=true

#========================
# 安装基础软件包
# 包括 jdk wget unzip ca-certificates tzdata...
#========================
RUN apt-get -qqy update \
  && apt-get -qqy --no-install-recommends install \
    bzip2 \
    ca-certificates \
    tzdata \
    sudo \
    unzip \
    wget \
    vim \
    git \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*

#===================
# 设置Timezone
# && sed -i 's|ZONE="Etc/UTC"|ZONE="Asia/Shanghai"|g' /etc/sysconfig/clock \
# && echo 'Asia/Shanghai' >> /etc/timezone \
# && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
#===================
ENV TZ "Asia/Shanghai"
RUN echo "${TZ}" > /etc/timezone \
  && dpkg-reconfigure --frontend noninteractive tzdata

CMD ["/bin/bash"]
