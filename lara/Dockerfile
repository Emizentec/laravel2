FROM php:8.1-fpm

WORKDIR /var/lib/jenkins/workspace/laravel2/lara

RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    zip \
    unzip

RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY . .

RUN composer install

RUN  /var/lib/jenkins/workspace/laravel2/lara/storage \
    /var/lib/jenkins/workspace/laravel2/lara/bootstrap/cache

EXPOSE 3016
CMD ["php-fpm"]
