# Version: 1
FROM  ubuntu:16.04
MAINTAINER Jose Agraz

# System Dependencies.
RUN apt update
RUN apt install -y nano git apache2 curl
RUN apt install -y software-properties-common python-software-properties

#####  PHP5.6  #####
RUN apt-get update
RUN LC_ALL=C.UTF-8 add-apt-repository -y ppa:ondrej/php && apt-get update && apt-get install -y php5.6
RUN apt-get install -y php5.6-curl php5.6-pgsql php5.6-intl php5.6-cli libapache2-mod-php5.6 php5.6-apc php5.6-xml php5.6-mysql php5.6-odbc php5.6-mcrypt php5.6-mbstring net-tools iputils-ping zip php5.6-bcmath
RUN a2enmod php5.6
RUN service apache2 restart
RUN update-alternatives --set php /usr/bin/php5.6
####################

#####  SSL #####
RUN a2enmod ssl && mkdir /etc/apache2/ssl
################

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN service apache2 restart

WORKDIR /var/www/html/
EXPOSE 8000
CMD /usr/sbin/apache2ctl -D FOREGROUND
