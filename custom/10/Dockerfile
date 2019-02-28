FROM php:7-fpm

RUN apt-get update \
  && apt-get install -y git libpng-dev wget zlib1g-dev \
  && docker-php-ext-install gd pdo_mysql zip \
  && rm -rf /var/lib/apt/lists/*

COPY bin bin

RUN ./bin/install_composer \
  && mv composer.phar /usr/local/bin/composer

RUN rm -r bin

RUN composer config -g repo.packagist composer https://packagist.laravel-china.org

ENV PATH="${PATH}:./vendor/bin"

RUN echo 'alias hey="php artisan"' >> ~/.bashrc

# /var/www/html
WORKDIR /usr/share/nginx/html

EXPOSE 9000


