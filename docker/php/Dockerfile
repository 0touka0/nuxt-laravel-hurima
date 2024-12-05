FROM php:8.2-fpm

COPY php.ini /usr/local/etc/php/

# 必要なパッケージをインストール
RUN apt update \
    && apt install -y default-mysql-client zlib1g-dev libzip-dev unzip libpng-dev libjpeg-dev libfreetype6-dev libmagickwand-dev --no-install-recommends \
    && docker-php-ext-configure gd --with-jpeg --with-freetype \
    && docker-php-ext-install pdo_mysql zip gd \
    && docker-php-ext-enable gd \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Composer をインストールして最新バージョンに更新
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer self-update

# StripeのPHP SDKをインストール
RUN composer require stripe/stripe-php

WORKDIR /var/www