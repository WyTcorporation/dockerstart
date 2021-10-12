# Для начала указываем исходный образ, он будет использован как основа
FROM php:7.4-fpm

# RUN выполняет идущую за ней команду в контексте нашего образа.
# В данном случае мы установим некоторые зависимости и модули PHP.
# Для установки модулей используем команду docker-php-ext-install.
# На каждый RUN создается новый слой в образе, поэтому рекомендуется объединять команды.
RUN apt-get update && apt-get install -y \
        curl \
        wget \
        git \
        libfreetype6-dev \
        libonig-dev \
        libpq-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libzip-dev \
        libxml2-dev \
        librabbitmq-dev \
	libssl-dev \
        vim \
        unzip \
    && pecl install mcrypt-1.0.3 \
    && docker-php-ext-install -j$(nproc) iconv \
        mbstring \
        mysqli \
        pdo_mysql \
#          bcmath\
#          bz2\
#          calendar\
#          ctype\
#          curl\
#          dba\
#          dom\
#          enchant\
#          exif\
#          fileinfo\
#          filter\
#          ftp\
#          gd\
#          gettext\
#          gmp\
#          hash\
#          imap\
#          interbase\
#          intl\
#          json\
#          ldap\
#          mbstring\
#          mcrypt\
#          mysqli\
#          oci8\
#          odbc\
#          opcache\
#          pcntl\
#          pdo\
#          pdo_dblib\
#          pdo_firebird\
#          pdo_mysql\
#          pdo_oci\
#          pdo_odbc\
#          pdo_pgsql\
#          pdo_sqlite\
#          pgsql\
#          phar\
#          posix\
#          pspell\
#          readline\
#          recode\
#          reflection\
#          session\
#          shmop\
#          simplexml\
#          snmp\
#          soap\
#          sockets\
#          spl\
#          standard\
#          sysvmsg\
#          sysvsem\
#          sysvshm\
#          tidy\
#          tokenizer\
#          wddx\
#          xml\
#          xmlreader\
#          xmlrpc\
#          xmlwriter\
#          xsl\
#          zip\
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-enable mcrypt

RUN pecl install mongodb && docker-php-ext-enable mongodb
RUN pecl install amqp && docker-php-ext-enable amqp 

RUN pecl install redis-5.1.1 \
    && pecl install xdebug-2.8.1 \
    && docker-php-ext-enable redis xdebug

# Куда же без composer'а.
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Добавим свой php.ini, можем в нем определять свои значения конфига
ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

# Указываем рабочую директорию для PHP
WORKDIR /var/www

# Запускаем контейнер
# Из документации: The main purpose of a CMD is to provide defaults for an executing container. These defaults can include an executable,
# or they can omit the executable, in which case you must specify an ENTRYPOINT instruction as well.
CMD ["php-fpm"]
