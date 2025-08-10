FROM jakzal/phpqa:1.97.6-php8.3-alpine

RUN apk update \
    && apk upgrade \
    && apk add --no-cache \
        freetype-dev \
        libpng-dev \
        jpeg-dev \
        libjpeg-turbo-dev \
        imagemagick-dev \
        imagemagick \
        autoconf \
        g++ \
        make \
        pkgconfig
RUN docker-php-ext-install gd
RUN docker-php-ext-install exif
RUN apk add --no-cache php83-pecl-imagick \
    && ln -s /usr/lib/php83/modules/imagick.so /usr/local/lib/php/extensions/no-debug-non-zts-20230831/ \
    && docker-php-ext-enable imagick
