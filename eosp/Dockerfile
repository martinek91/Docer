FROM eboraas/laravel:stretch
MAINTAINER Martinek91

# RUN apt-get update && apt-get -y upgrade && apt-get -y autoremove && apt-get clean && rm -r /var/lib/apt/lists/*

RUN mkdir $HOME/eosp
RUN cd $HOME/eosp
RUN git clone https://git.wmi.amu.edu.pl/s421507/eOSP2.git master
RUN /bin/cp -r $HOME/eosp/* /var/www/laravel/
RUN chown -R www-data:www-data /var/www/laravel
RUN chmod -R 755 /var/www/laravel


EXPOSE 22
EXPOSE 80
EXPOSE 443

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
