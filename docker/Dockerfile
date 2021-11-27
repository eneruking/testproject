FROM php:7.4-apache
COPY ./php/php.ini /usr/local/etc/php/
COPY ./apache/*.conf /etc/apache2/sites-enabled/

# composerを使う際にマルチステージビルドを使う
COPY --from=composer /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_NO_INTERACTION 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin

RUN apt-get update && \
  # Vim
  apt-get install -y vim && \
  # unzip コマンド (composer create-project で必要)
  apt-get install -y unzip && \
  # PDO MySQL 拡張
  docker-php-ext-install pdo_mysql && \
  # mod_rewrite 有効化
  a2enmod rewrite && \
  # デバッグ実行のために必要
  pecl install xdebug && \
  docker-php-ext-enable xdebug && \
  apt-get install -y gnupg && \
  curl -sL https://deb.nodesource.com/setup_10.x | bash - && \
  apt-get install -y nodejs

WORKDIR /var/www/html
