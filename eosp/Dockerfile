FROM eboraas/apache-php:stretch
MAINTAINER Martinek91

RUN apt-get update && apt-get upgrade && apt-get -y install git curl php-json php-mbstring php-zip php-dom php-xml php-gd php-opcache && apt-get -y autoremove && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer

RUN mkdir $HOME/eosp
RUN cd $HOME/eosp && git clone https://git.wmi.amu.edu.pl/s421507/eOSP2.git master && mv * /var/www/laravel/
RUN cd /var/www/laravel && composer install && mv .env.example .env && php artisan key:generate
RUN sed -i 's/DB_HOST=127.0.0.1/DB_HOST=localhost/g' /var/www/laravel/.env
RUN chown -R www-data:www-data /var/www/laravel
RUN chmod -R 755 /var/www/laravel

#RUN cd /var/www/laravel/ && php artisan down
#RUN cd /var/www/laravel/ && php artisan config:clear
#RUN cd /var/www/laravel/ && php artisan migrate
#RUN cd /var/www/laravel/ && php artisan db:seed
#RUN cd /var/www/laravel/ && php artisan queue:restart
#RUN cd /var/www/laravel/ && php artisan cache:clear
#RUN cd /var/www/laravel/ && php artisan up


EXPOSE 22
EXPOSE 80
EXPOSE 443

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
