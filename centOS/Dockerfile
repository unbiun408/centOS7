# 使用CentOS 8作为基础镜像
FROM centos:8

# 设置环境变量
ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_DATABASE=mydb
ENV MYSQL_USER=user
ENV MYSQL_PASSWORD=password
ENV JAVA_HOME=/usr/java/latest
ENV PATH=$JAVA_HOME/bin:$PATH

# 安装必要的软件
RUN dnf -y update && \
    dnf install -y epel-release && \
    dnf install -y httpd mysql-server java-1.8.0-openjdk-devel nginx && \
    dnf clean all

# 启动MySQL服务
RUN systemctl enable mysqld

# 拷贝Nginx配置文件
COPY nginx.conf /etc/nginx/nginx.conf

# 暴露端口
EXPOSE 80 8080 3306

# 挂载卷
VOLUME ["/var/lib/mysql", "/var/www/html"]

# 启动脚本
CMD ["/bin/bash", "-c", "service mysqld start && httpd -D FOREGROUND & nginx -g 'daemon off;'"]
