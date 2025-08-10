FROM jakzal/phpqa:1.97-php8.2-alpine

RUN apk update \
    && apk upgrade \
    && apk add --no-cache \
        freetype-dev \
        libpng-dev \
        jpeg-dev \
        libjpeg-turbo-dev
RUN docker-php-ext-install gd
RUN docker-php-ext-install exif
