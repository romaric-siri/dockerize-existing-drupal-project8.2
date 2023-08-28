ARG PHP_VERSION=""
FROM php:${PHP_VERSION:+${PHP_VERSION}-}fpm-alpine

RUN apk update; \
    apk upgrade;
RUN apk add --update linux-headers

# Install gd library extension
RUN apk add libpng libpng-dev libjpeg-turbo-dev libwebp-dev zlib-dev libxpm-dev gd && docker-php-ext-install gd    

# Install MySql
RUN docker-php-ext-install mysqli pdo pdo_mysql

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer && \
    ln -s /root/.composer/vendor/bin/drush /usr/local/bin/drush

# Install Drush
RUN composer global require drush/drush && \
    composer global update 

	# PHP packages
RUN apk add --update \
        libressl \
        ca-certificates \
        openssh-client \
        rsync \
        git \
        curl \
        wget \
        gzip \
        tar \
        patch \
        perl \
        pcre \
        imap \
        imagemagick \
        mariadb-client \
        build-base \
        autoconf \
        libtool \
        pcre-dev \
        imagemagick-dev \
        php \
        php-fpm \
        php-opcache \
        php-session \
        php-dom \
        php-xml \
        php-xmlreader \
        php-ctype \
        php-ftp \
        php-gd \
        php-json \
        php-posix \
        php-curl \
        php-pdo \
        php-pdo_mysql \
        php-sockets \
        php-zlib \
        php-mysqli \
        php-sqlite3 \
        php-bz2 \
        php-phar \
        php-openssl \
        php-posix \
        php-zip \
        php-calendar \
        php-iconv \
        php-imap \
        php-soap \
        php-pear \
        php-mbstring \
        php-exif \
        php-xsl \
        php-ldap \
        php-bcmath \
	php82-pecl-xdebug

RUN pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini
