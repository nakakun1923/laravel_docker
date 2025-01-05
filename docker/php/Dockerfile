# PHPのイメージを指定
FROM php:8.2-fpm

# 必要な依存をインストール
RUN apt-get update && apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev zip git curl libzip-dev

# PHP拡張をインストール
RUN docker-php-ext-configure gd --with-freetype --with-jpeg && docker-php-ext-install gd pdo pdo_mysql zip

# Composerをインストール
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# 作業ディレクトリを設定
WORKDIR /var/www

# 必要なポートを公開
EXPOSE 9000

# 作業ディレクトリにファイルをコピー
COPY ../../src /var/www

# Laravelの依存関係をインストール
RUN composer install

CMD ["php-fpm"]