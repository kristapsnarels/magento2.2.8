FROM arm64v8/php:7.1-fpm

# Install dependencies
RUN apt-get update \
  && apt-get upgrade -y \
  && apt-get install -y --no-install-recommends \
  apt-utils \
  sendmail-bin \
  sendmail \
  sudo \
  iproute2 \
  git \
  gnupg2 \
  ca-certificates \
  lsb-release \
  software-properties-common \
  libbz2-dev \
  libjpeg62-turbo-dev \
  libpng-dev \
  libfreetype6-dev \
  libgeoip-dev \
  wget \
  libgmp-dev \
  libgpgme11-dev \
  libmagickwand-dev \
  libmagickcore-dev \
  libc-client-dev \
  libkrb5-dev \
  libicu-dev \
  libldap2-dev \
  libpspell-dev \
  librecode0 \
  librecode-dev \
  libssh2-1 \
  libssh2-1-dev \
  libtidy-dev \
  libxslt1-dev \
  libyaml-dev \
  libzip-dev \
  zip \
  && rm -rf /var/lib/apt/lists/*

# Configure the gd library
RUN docker-php-ext-configure \
  gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-configure \
  imap --with-kerberos --with-imap-ssl
RUN docker-php-ext-configure \
  opcache --enable-opcache
RUN docker-php-ext-configure \
  zip --with-libzip

# Install required PHP extensions
RUN docker-php-ext-install -j$(nproc) \
  bcmath \
  bz2 \
  calendar \
  dom \
  exif \
  gd \
  gettext \
  gmp \
  imap \
  intl \
  mysqli \
  opcache \
  pdo_mysql \
  pspell \
  recode \
  shmop \
  soap \
  sockets \
  sysvmsg \
  sysvsem \
  sysvshm \
  tidy \
  mbstring \
  xmlrpc \
  xsl \
  zip \
  pcntl

# Setup Xdebug
RUN pecl install xdebug-2.7.0
RUN docker-php-ext-enable xdebug

# Setup Composer
ENV COMPOSER_ALLOW_SUPERUSER 1
RUN curl -sS https://getcomposer.org/installer | php -- \
        --version=1.10.23 \
        --filename=composer \
        --install-dir=/usr/local/bin && \
        echo "alias composer='composer'" >> /root/.bashrc

COPY config/php-fpm.ini /usr/local/etc/php/conf.d/customs.ini
COPY config/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
COPY config/php-fpm.conf /usr/local/etc/php-fpm.d
