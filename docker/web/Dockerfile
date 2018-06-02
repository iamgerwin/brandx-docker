FROM php:7.1-apache
MAINTAINER iamgerwin

COPY ./sites-available/000-default.conf /etc/apache2/sites-available/000-default.conf

RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng12-dev \
    libxml2-dev \
    curl \
    wget \
    zip \
    unzip \
    git \
    cron \
    vim \
    nano \
    tmux \
    zsh \
    && docker-php-ext-install -j$(nproc) iconv mcrypt pdo pdo_mysql mysqli zip soap mbstring \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN a2enmod rewrite

# PHP Debug
RUN pecl install xdebug

COPY xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

# Install composer
COPY --from=composer:1.6.3 /usr/bin/composer /usr/bin/composer

RUN composer config --global process-timeout 2000

EXPOSE 80
