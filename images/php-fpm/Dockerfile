FROM php:7.3-fpm
LABEL maintainer="STAR Z <zx1625437980@gmail.com>"

ENV TZ="Asia\Shanghai"
RUN date -R

WORKDIR /var/www

RUN apt-get update --fix-missing && apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev zlib1g-dev libzip-dev zip unzip \
  && docker-php-ext-configure gd --with-freetype-dir=/usr/inclue --with-jpeg-dir=/usr/inclue/jpeg \
  && docker-php-ext-install gd mysqli opcache pdo_mysql zip

RUN pecl install redis \
  && pecl install mongodb \
  && pecl install swoole \
  && docker-php-ext-enable redis mongodb swoole

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
     && php composer-setup.php \
     && php -r "unlink('composer-setup.php');" \
     && mv composer.phar /usr/local/bin/composer \
     && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

RUN apt-get install -y git

RUN rm -rf /var/cache/apt/* \
  && rm -rf /var/lib/apt/lists/* 

RUN mkdir /var/lib/sessions \
  && chmod o=rwx -R /var/lib/sessions

CMD [ "php-fpm" ]