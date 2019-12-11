FROM php:7.2-fpm

COPY php.ini /usr/local/etc/php/

RUN apt-get update \
    && apt-get install -y libicu-dev zip unzip curl zlib1g-dev libpng-dev vim procps git \
    && docker-php-ext-install intl opcache \
    && docker-php-ext-enable intl opcache \
    && docker-php-ext-install pdo pdo_mysql mysqli\
    && docker-php-ext-install mbstring \
    && docker-php-ext-install gd \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN groupadd nginx

RUN useradd -ms /bin/bash -g nginx www-user \
    && echo "www-user:phpfpm" | chpasswd

RUN chown -R www-user:nginx /var/www/ \
    && chown -R www-user:nginx /var/run/ \
    && chown -R www-user:nginx /var/log/

USER www-user