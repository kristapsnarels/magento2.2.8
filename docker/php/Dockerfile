FROM php:7.1-fpm
RUN apt-get update && apt-get install -y zlib1g-dev libpng-dev libfreetype6-dev libjpeg62-turbo-dev \
    zlib1g-dev libicu-dev g++ libxml2 libxml2-dev mcrypt libmcrypt-dev libxslt1-dev git sudo libbz2-dev libzip-dev
RUN pecl install xdebug-2.7.0
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install pdo_mysql mysqli intl dom mbstring gd soap mcrypt zip xsl bcmath exif bz2 opcache \
    && docker-php-ext-enable xdebug
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl -sS https://getcomposer.org/installer | php -- \
        --version=1.10.23 \
        --filename=composer \
        --install-dir=/usr/local/bin && \
        echo "alias composer='composer'" >> /root/.bashrc
RUN rm -rf /var/www
VOLUME /var/www/