FROM nginx:1.15-alpine

#COPY docker/server/conf.d/default.conf /etc/nginx/conf.d/default.conf
COPY . /var/www/app/

ADD nginx.conf /etc/nginx/
ADD docker/server/symfony.conf /etc/nginx/sites-available/

RUN ln -s /etc/nginx/sites-available/symfony.conf /etc/nginx/sites-enabled/symfony
RUN rm /etc/nginx/sites-enabled/default

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443