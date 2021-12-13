#1.Base Image
FROM alpine:3.15.0

LABEL authors="Borer" documentation="https://github.com/JanU-YieG/docker-run-env/wiki"

# ensure www-data user exists
#RUN set -x \
#	&& addgroup -g 82  -S www-data \
#	&& adduser -u 82 -D -S -G www-data www-data

# Environments
ENV TIMEZONE            Asia/Shanghai
# ENV PHP_MEMORY_LIMIT    512M
# ENV MAX_UPLOAD          50M
# ENV PHP_MAX_FILE_UPLOAD 200
# ENV PHP_MAX_POST        100M
# ENV COMPOSER_ALLOW_SUPERUSER 1

#2.ADD-PHP-FPM

# Mirror mirror switch to Alpine Linux - http://dl-4.alpinelinux.org/alpine/
RUN apk update \
    && apk upgrade \
    && apk add \
        curl \
        tzdata \
        php8-fpm\
        php8 \
        php8-dev \
        php8-apcu \
        php8-bcmath \
        php8-xmlwriter \
        php8-ctype \
        php8-curl \
        php8-exif \
        php8-iconv \
        php8-intl \
        php8-json \
        php8-mbstring\
        php8-opcache \
        php8-openssl \
        php8-pcntl \
        php8-pdo \
        php8-mysqlnd \
        php8-mysqli \
        php8-pdo_mysql \
        php8-pdo_pgsql \
        php8-phar \
        php8-posix \
        php8-session \
        php8-xml \
        php8-simplexml \
        # php8-mcrypt \
        php8-xsl \
        php8-zip \
        php8-zlib \
        php8-dom \
        php8-redis\
        php8-tokenizer \
        php8-gd \
        php8-mongodb\
        php8-fileinfo \
        # php8-zmq \
        # php8-memcached \
        php8-xmlreader \
    && cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime \
    && echo "${TIMEZONE}" > /etc/timezone \
    && apk del tzdata \
    && rm -rf /var/cache/apk/* \
    && mkdir -p /usr/local/var/log/php8/  \
    && mkdir -p /usr/local/var/run/

EXPOSE 9000

# https://github.com/docker-library/php/issues/240
# https://gist.github.com/guillemcanal/be3db96d3caa315b4e2b8259cab7d07e
# https://forum.alpinelinux.org/forum/installation/php-iconv-issue
#####
# COPY ./php/php-fpm.conf /etc/php7/
# COPY ./php/www.conf /etc/php7/php-fpm.d/
#####

#RUN apk add --no-cache --repository http://dl-3.alpinelinux.org/alpine/edge/testing gnu-libiconv
#ENV LD_PRELOAD /usr/lib/preloadable_libiconv.so php
#RUN rm -rf /var/cache/apk/*

# Set environments
#####
# RUN sed -i "s|;*date.timezone =.*|date.timezone = ${TIMEZONE}|i" /etc/php7/php.ini && \
	# sed -i "s|;*memory_limit =.*|memory_limit = ${PHP_MEMORY_LIMIT}|i" /etc/php7/php.ini && \
	# sed -i "s|;*upload_max_filesize =.*|upload_max_filesize = ${MAX_UPLOAD}|i" /etc/php7/php.ini && \
	# sed -i "s|;*max_file_uploads =.*|max_file_uploads = ${PHP_MAX_FILE_UPLOAD}|i" /etc/php7/php.ini && \
	# sed -i "s|;*post_max_size =.*|post_max_size = ${PHP_MAX_POST}|i" /etc/php7/php.ini && \
	# sed -i "s|;*cgi.fix_pathinfo=.*|cgi.fix_pathinfo= 0|i" /etc/php7/php.ini
#####

#3.Install-Composer
#####
RUN curl -sS https://getcomposer.org/installer | \
    php -- --install-dir=/usr/bin/ --filename=composer



#4.ADD-NGINX
#####
RUN apk add nginx
# COPY ./nginx/conf.d/default.conf /etc/nginx/conf.d/
# COPY ./nginx/nginx.conf /etc/nginx/
# COPY ./nginx/cert/ /etc/nginx/cert/

# RUN mkdir -p /usr/share/nginx/html/public/
# COPY ./php/index.php /usr/share/nginx/html/public/
#####
#RUN mkdir -p /run/nginx
#RUN touch /run/nginx/nginx.pid
# Expose volumes
EXPOSE 80

#####
# VOLUME ["/usr/share/nginx/html", "/usr/local/var/log/php7", "/var/run/"]
# WORKDIR /usr/share/nginx/html
#####

#5.ADD-SUPERVISOR
##### 
# RUN apk add supervisor \
 # && rm -rf /var/cache/apk/*
#####

# Define mountable directories.
#####
# VOLUME ["/etc/supervisor/conf.d", "/var/log/supervisor/"]
# COPY ./supervisor/conf.d/ /etc/supervisor/conf.d/
#####

#6.ADD-CRONTABS
#####
# COPY ./crontabs/default /var/spool/cron/crontabs/
# RUN cat /var/spool/cron/crontabs/default >> /var/spool/cron/crontabs/root
# RUN mkdir -p /var/log/cron \
 # && touch /var/log/cron/cron.log

# VOLUME /var/log/cron
#####

#7.ADD-REDIS
# RUN apk add redis

#8.ADD-MARIADB
RUN apk add mariadb=10.6.5-1

#设置环境变量，便于管理
ENV MARIADB_USER root
ENV MARIADB_PASS 123456
##初始化数据库
#COPY ./mariadb/db_init.sh /etc/
#RUN chmod 775 /etc/db_init.sh
#RUN /etc/db_init.sh

#导出端口
EXPOSE 3306

#添加启动文件
#ADD ./mariadb/run.sh /root/run.sh
#RUN chmod 775 /root/run.sh
#设置默认启动命令
#CMD ["/root/run.sh"]

#9.添加启动脚本
# Define working directory.
#####
# WORKDIR /usr/share/nginx/html
# COPY ./entrypoint.sh /usr/share/nginx/html/
# RUN chmod +x /usr/share/nginx/html/entrypoint.sh
#####

# VOLUMES
VOLUME ["/var/lib/mysql","/var/log/mysql","/var/www/html","/usr/share/nginx/html","/data"]
#CMD ["supervisord", "--nodaemon", "--configuration", "/etc/supervisor/conf.d/supervisord.conf"]
# ENTRYPOINT ["./entrypoint.sh"]
