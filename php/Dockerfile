FROM php:8.1.8-fpm

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php composer-setup.php \
  && php -r "unlink('composer-setup.php');" \
  && chmod +x composer.phar \
  && mv composer.phar /usr/local/bin/composer


RUN apt-get update && apt-get install -y \
    git build-essential libmcrypt-dev libreadline-dev zip unzip \
    libssl-dev zlib1g-dev libpng-dev libjpeg-dev libfreetype6-dev \
    jpegoptim optipng pngquant gifsicle webp libzip-dev zlib1g-dev zip unzip libxml2-dev libicu-dev

RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/

RUN docker-php-ext-install pdo_mysql pcntl bcmath gd soap 

RUN docker-php-ext-configure zip \
    && docker-php-ext-install zip

RUN pecl install mongodb
RUN docker-php-ext-enable mongodb

RUN docker-php-ext-configure intl \
      && docker-php-ext-install intl

#WORKDIR /var/www/app

CMD ["/usr/local/sbin/php-fpm"]