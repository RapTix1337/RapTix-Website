FROM php:8.1-fpm

RUN apt update \
    && apt install -y zlib1g-dev libpng-dev libjpeg-dev libwebp-dev g++ git libicu-dev zip libzip-dev \
    && docker-php-ext-install intl opcache pdo pdo_mysql bcmath \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-configure zip \
    && docker-php-ext-install zip

WORKDIR /var/www/html
COPY ./composer.json /var/www/html/composer.json

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | bash && apt install symfony-cli