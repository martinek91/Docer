FROM eboraas/laravel:stretch
MAINTAINER Martinek91

# RUN apt-get update && apt-get -y upgrade && apt-get -y autoremove && apt-get clean && rm -r /var/lib/apt/lists/*

RUN mkdir $HOME/eosp
RUN cd /var/www/laravel/ && php artisan down
RUN cd $HOME/eosp && git clone https://git.wmi.amu.edu.pl/s421507/eOSP2.git master && mv * /var/www/laravel/
RUN sed -i 's/DB_HOST=127.0.0.1/DB_HOST=localhost/g' /var/www/laravel/.env
RUN chown -R www-data:www-data /var/www/laravel
RUN chmod -R 755 /var/www/laravel
RUN cd /var/www/laravel/ && php artisan config:clear
RUN cd /var/www/laravel/ && php artisan migrate
RUN cd /var/www/laravel/ && php artisan db:seed
RUN cd /var/www/laravel/ && php artisan queue:restart
RUN cd /var/www/laravel/ && php artisan cache:clear
RUN cd /var/www/laravel/ && php artisan up


EXPOSE 22
EXPOSE 80
EXPOSE 443

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
