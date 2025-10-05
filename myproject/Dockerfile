FROM php:8.2-fpm

# ติดตั้ง extension ที่ Laravel ต้องใช้
RUN docker-php-ext-install pdo pdo_mysql

# ตั้ง working directory
WORKDIR /var/www/html

# คัดลอกไฟล์ทั้งหมดเข้า container
COPY . .

# ติดตั้ง composer
RUN apt-get update && apt-get install -y unzip git \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer install

# เปิดพอร์ต 8000
EXPOSE 8000

# รัน Laravel server
CMD ["php", "artisan", "serve", "--host=0.0.0.0"]
