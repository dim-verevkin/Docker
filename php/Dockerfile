FROM php:8.1-fpm-alpine

RUN docker-php-ext-install mysqli pdo pdo_mysql

COPY --from=composer:2.3.9 /usr/bin/composer /usr/bin/composer

RUN mkdir -p /app && chown www-data:www-data /app
WORKDIR /app

USER www-data:www-data

COPY --chown=www-data:www-data ./composer.* ./
RUN composer install --no-dev --optimize-autoloader

COPY --chown=www-data:www-data . .
