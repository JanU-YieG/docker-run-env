# Auto-generated via Ansible: edit build/ansible/DOCKERFILES/Dockerfile-base.j2 instead.
FROM php:8-fpm-alpine
# MAINTAINER "borer" <borer@everythingcli.org>


###
### Labels
###
# https://github.com/opencontainers/image-spec/blob/master/annotations.md
#LABEL "org.opencontainers.image.created"=""
#LABEL "org.opencontainers.image.version"=""
#LABEL "org.opencontainers.image.revision"=""
# LABEL "maintainer"="cytopia <cytopia@everythingcli.org>"
# LABEL "org.opencontainers.image.authors"="cytopia <cytopia@everythingcli.org>"
# LABEL "org.opencontainers.image.url"="https://github.com/devilbox/docker-php-fpm"
# LABEL "org.opencontainers.image.documentation"="https://github.com/devilbox/docker-php-fpm"
# LABEL "org.opencontainers.image.source"="https://github.com/devilbox/docker-php-fpm"
# LABEL "org.opencontainers.image.vendor"="devilbox"
# LABEL "org.opencontainers.image.licenses"="MIT"
# LABEL "org.opencontainers.image.ref.name"="7.4-base"
# LABEL "org.opencontainers.image.title"="PHP-FPM 7.4-base"
# LABEL "org.opencontainers.image.description"="PHP-FPM 7.4-base"


###
### Envs
###
# ENV MY_USER="borer" \
    # MY_GROUP="borer" \
    # MY_UID="1000" \
    # MY_GID="1000" \
    # PHP_VERSION="8.0"  \
ENV    TIMEZONE="Asia/Shanghai"

###
### User/Group
###
# RUN set -eux \
    # && addgroup -g ${MY_GID} ${MY_GROUP} \
    # && adduser -u ${MY_UID} ${MY_USER} ${MY_GROUP}


###
### Upgrade (install ps)
###
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
    # && apk update \
    # && apk upgrade \
    # && docker-php-source extract \
    && docker-php-ext-install \
        pdo_mysql
        # mbstring \
    # && docker-php-ext-enable \
        # openssl \
        # tokenizer \
        # xml \
        # json \
        # bcmath \
        # ctype \
        # PDO \
        # fileinfo
        # bcmath \
        # ctype \
        # # curl \
        # # exif \
        # # iconv \
        # # intl \
        # json \
        # # apcu \
        # # xmlwriter \
        # mbstring \
        # # opcache \
        # openssl \
        # # pcntl \
        # pdo \
        # # mysqlnd \
        # # mysqli \
        # # pdo_pgsql \
        # # phar \
        # # posix \
        # # session \
        # xml \
        # # simplexml \
        # # mcrypt \
        # # xsl \
        # # zip \
        # # zlib \
        # # dom \
        # # redis \
        # tokenizer \
        # # gd \
        # # mongodb \
        # fileinfo \
        # # memcached \
        # # xmlreader \
        # # zmq \
    # && cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime \
    # && echo "${TIMEZONE}" > /etc/timezone \
    # && mkdir -p /usr/local/var/log/php8/  \
    # && mkdir -p /usr/local/var/run/
    # && rm -rf /var/lib/apk/lists/*
# RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
    # && set -eux \
	# # && DEBIAN_FRONTEND=noninteractive apt-get update -qq \
	# # && DEBIAN_FRONTEND=noninteractive apt-get install -qq -y --no-install-recommends --no-install-suggests procps \
    # && apk update \
    # && apk upgrade \
    # && apk add \
        # curl \
        # tzdata \
        # # php8-fpm\
        # # php8 \
        # php8-dev \
        # # php8-apcu \
        # php8-bcmath \
        # php8-xmlwriter \
        # php8-ctype \
        # php8-curl \
        # php8-exif \
        # php8-iconv \
        # php8-intl \
        # php8-json \
        # php8-mbstring\
        # php8-opcache \
        # php8-openssl \
        # php8-pcntl \
        # php8-pdo \
        # php8-mysqlnd \
        # php8-mysqli \
        # php8-pdo_mysql \
        # php8-pdo_pgsql \
        # php8-phar \
        # php8-posix \
        # php8-session \
        # php8-xml \
        # php8-simplexml \
        # # php8-mcrypt \
        # php8-xsl \
        # php8-zip \
        # php8-zlib \
        # php8-dom \
        # php8-redis\
        # php8-tokenizer \
        # php8-gd \
        # php8-mongodb\
        # php8-fileinfo \
        # # php8-zmq \
        # # php8-memcached \
        # php8-xmlreader \
    # && cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime \
    # && echo "${TIMEZONE}" > /etc/timezone \
    # && mkdir -p /usr/local/var/log/php8/  \
    # && mkdir -p /usr/local/var/run/ \
	# && rm -rf /var/lib/apt/lists/*


###
### Configure
###
# RUN set -eux \
	# && rm -rf /usr/local/etc/php-fpm.d \
	# && mkdir -p /usr/local/etc/php-fpm.d \
	# && mkdir -p /var/lib/php/session \
	# && mkdir -p /var/lib/php/wsdlcache \
	# && chown -R borer:borer /var/lib/php/session \
	# && chown -R borer:borer /var/lib/php/wsdlcache


###
### Copy files
###
# COPY ./data/php-ini.d/php-7.4.ini /usr/local/etc/php/conf.d/xxx-devilbox-default-php.ini
# COPY ./data/php-fpm.conf/php-fpm-7.4.conf /usr/local/etc/php-fpm.conf

# COPY ./data/docker-entrypoint.sh /docker-entrypoint.sh
# COPY ./data/docker-entrypoint.d /docker-entrypoint.d


###
### Verify
###
# RUN set -eux \
	# && echo "date.timezone=UTC" > /usr/local/etc/php/php.ini \
	# && php -v | grep -oE 'PHP\s[.0-9]+' | grep -oE '[.0-9]+' | grep '^7.4' \
	# && /usr/local/sbin/php-fpm --test \
	# \
	# && PHP_ERROR="$( php -v 2>&1 1>/dev/null )" \
	# && if [ -n "${PHP_ERROR}" ]; then echo "${PHP_ERROR}"; false; fi \
	# && PHP_ERROR="$( php -i 2>&1 1>/dev/null )" \
	# && if [ -n "${PHP_ERROR}" ]; then echo "${PHP_ERROR}"; false; fi \
	# \
	# && PHP_FPM_ERROR="$( php-fpm -v 2>&1 1>/dev/null )" \
	# && if [ -n "${PHP_FPM_ERROR}" ]; then echo "${PHP_FPM_ERROR}"; false; fi \
	# && PHP_FPM_ERROR="$( php-fpm -i 2>&1 1>/dev/null )" \
	# && if [ -n "${PHP_FPM_ERROR}" ]; then echo "${PHP_FPM_ERROR}"; false; fi \
	# && rm -f /usr/local/etc/php/php.ini


###
### Ports
###
EXPOSE 9000


###
### Entrypoint
###
CMD ["/usr/local/sbin/php-fpm"]
# ENTRYPOINT ["/docker-entrypoint.sh"]
