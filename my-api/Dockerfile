# Dockerfile (di dalam my-api/)
FROM php:8.2-fpm

# Install dependencies
RUN apt-get update && apt-get install -y \
    git zip unzip curl libpng-dev libonig-dev libxml2-dev libzip-dev \
    libpq-dev libjpeg-dev libfreetype6-dev \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && docker-php-ext-install pdo pdo_mysql mbstring zip exif pcntl


# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working dir
WORKDIR /var/www

# Salin project
COPY . .

# Install Laravel deps
RUN composer install

# Set permission
RUN chown -R www-data:www-data /var/www

# Expose port (kalau pakai artisan serve)
EXPOSE 8000

CMD php artisan serve --host=0.0.0.0 --port=8000
