FROM ubuntu:latest
MAINTAINER Martinek91

RUN apt-get update
RUN apt-get -y install software-properties-common
RUN add-apt-repository ppa:ondrej/php
RUN apt-get update
RUN apt-get -y upgrade
RUN apt-get -y install apache2
RUN apt-get -y install php7.4

RUN apt-get -y autoremove
RUN apt-get clean 
RUN rm -rf /var/lib/apt/lists/*

#RUN apt-get update
#RUN apt-get install software-properties-common -y
#RUN add-apt-repository ppa:ondrej/php
#RUN add-apt-repository ppa:ondrej/apache2
#RUN apt-get update && apt-get upgrade -y && apt-get -y install git curl php7.3 php7.3-mysql libapache2-mod-php7.3 php7.3-json php7.3-mbstring php7.3-zip php7.3-dom php7.3-xml php7.3-gd php7.3-opcache && apt-get -y autoremove && apt-get clean && rm -rf /var/lib/apt/lists/*
#RUN a2enmod mpm_prefork
#RUN a2enmod rewrite
#RUN curl -sS https://getcomposer.org/installer | php
#RUN mv composer.phar /usr/local/bin/composer
#RUN chmod +x /usr/local/bin/composer
#RUN mkdir $HOME/eosp
#RUN cd $HOME/eosp && git clone https://git.wmi.amu.edu.pl/s421507/eOSP2.git master && mv * /var/www/laravel/
#RUN cd /var/www/laravel && composer install 
#RUN cd /var/www/laravel && mv .env.example .env && php artisan key:generate
#RUN sed -i 's/DB_HOST=127.0.0.1/DB_HOST=localhost/g' /var/www/laravel/.env
#RUN chown -R www-data:www-data /var/www/laravel
#RUN chmod -R 755 /var/www/laravel
#RUN cd /var/www/laravel/ && php artisan migrate
#RUN cd /var/www/laravel/ && php artisan db:seed
#RUN cd /var/www/laravel/ && php artisan serve

#RUN cd /var/www/laravel/ && php artisan down
#RUN cd /var/www/laravel/ && php artisan config:clear
#RUN cd /var/www/laravel/ && php artisan queue:restart
#RUN cd /var/www/laravel/ && php artisan cache:clear
#RUN cd /var/www/laravel/ && php artisan up


EXPOSE 22
EXPOSE 80
EXPOSE 443

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
