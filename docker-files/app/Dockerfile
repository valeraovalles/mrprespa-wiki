# Version: 1
FROM  ubuntu:16.04
MAINTAINER Jhoan Valera

# System Dependencies.
RUN apt update
RUN apt install -y nano git apache2 curl
RUN apt install -y software-properties-common python-software-properties

#####  PHP  #####
RUN apt-get update
RUN LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php && apt-get update && apt-get install -y php
RUN apt-get install -y php-curl php-pgsql php-intl php-cli libapache2-mod-php php-xml php-mysql php-odbc php-mcrypt php-mbstring net-tools iputils-ping zip php-bcmath
####################

#####  SSL #####
RUN a2enmod ssl && mkdir /etc/apache2/ssl
################

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN service apache2 restart

WORKDIR /var/www/html/
EXPOSE 8000
CMD /usr/sbin/apache2ctl -D FOREGROUND
