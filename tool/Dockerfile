FROM registry.cn-hangzhou.aliyuncs.com/web_lnmp/php:7.4.33-fpm


# 镜像源换为阿里云镜像
RUN sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list \
    && sed -i 's/security.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list \
    && apt-get update

# 安装composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# 安装supervisord
RUN apt-get update && apt-get install -y supervisor && apt-get install -y cron
RUN mkdir -p /var/log/supervisor

COPY supervisord.conf /etc/supervisor/supervisord.conf

#设置系统时区为北京
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime


ENTRYPOINT ["supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]

