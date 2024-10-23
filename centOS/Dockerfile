# 使用CentOS作为基础镜像
FROM centos:7

# 设置维护者信息
LABEL maintainer="2514770920@qq.com"

# 安装EPEL库和MySQL
RUN yum -y update && \
    yum -y install epel-release && \
    yum -y install https://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm && \
    yum -y install mysql-server && \
    yum clean all

# 暴露MySQL端口
EXPOSE 3306

# 启动MySQL服务
CMD ["mysqld"]
