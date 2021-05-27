
FROM php:7.3-fpm

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
	    libpng-dev \
	    libonig-dev \
	    libzip-dev \
	    libmcrypt-dev \
        && pecl install mcrypt-1.0.3 \
	    && docker-php-ext-enable mcrypt \
        && docker-php-ext-install -j$(nproc) iconv mbstring mysqli pdo_mysql zip \
        && docker-php-ext-install -j$(nproc) gd 
ARG CONFIG
COPY ./conf/${CONFIG}.conf /usr/local/etc/php-fpm.d/zz-docker.conf
COPY ./conf /var/www/htdocs/files

