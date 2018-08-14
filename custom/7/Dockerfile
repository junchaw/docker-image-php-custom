FROM php:7-fpm

RUN apt-get update \
  && apt-get install -y git libpng-dev zlib1g-dev \
  && docker-php-ext-install gd pdo_mysql zip \
  && rm -rf /var/lib/apt/lists/*

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
  && php composer-setup.php \
  && php -r "unlink('composer-setup.php');" \
  && mv composer.phar /usr/local/bin/composer \
  && composer config -g repo.packagist composer https://packagist.laravel-china.org

RUN echo 'alias hey="php artisan"' >> ~/.bashrc

# /var/www/html
WORKDIR /usr/share/nginx/html

EXPOSE 9000


