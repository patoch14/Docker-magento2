FROM php:7.1-fpm

RUN apt-get update && apt-get install -y libpng-dev libwebp-dev libjpeg62-turbo-dev libxpm-dev libmcrypt-dev libjpeg-dev libpq-dev zlib1g-dev libicu-dev libfreetype6-dev \
&& rm -rf /var/lib/apt/lists/* \
&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr --with-gd --with-webp-dir --with-jpeg-dir --with-png-dir --with-zlib-dir --with-xpm-dir --with-freetype-dir --enable-gd-native-ttf \
&& docker-php-ext-configure intl \
&& docker-php-ext-install gd mbstring pdo pdo_mysql pdo_pgsql iconv mcrypt intl

RUN apt-get update && apt-get -y install nano dos2unix

COPY ./setup-upgrade /usr/local/bin/setup-upgrade
RUN dos2unix /usr/local/bin/setup-upgrade
RUN chmod +x /usr/local/bin/setup-upgrade

COPY ./cache-clean /usr/local/bin/cache-clean
RUN dos2unix /usr/local/bin/cache-clean
RUN chmod +x /usr/local/bin/cache-clean

COPY ./setup-compile /usr/local/bin/setup-compile
RUN dos2unix /usr/local/bin/setup-compile
RUN chmod +x /usr/local/bin/setup-compile