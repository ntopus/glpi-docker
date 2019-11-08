FROM php:7.1-fpm

# Diretório do GLPI
ENV glpi /var/www/html/glpi

# Instalando pacotes do PHP
RUN apt update
RUN apt -y install libpng-dev libxml2-dev libc-client-dev libkrb5-dev libldb-dev libldap2-dev wget
RUN docker-php-ext-install json mbstring mysqli pdo_mysql session dom xml gd
RUN docker-php-ext-configure imap --with-kerberos --with-imap-ssl 
RUN docker-php-ext-install imap ldap opcache xmlrpc exif
RUN pecl install apcu
RUN echo extension=apcu.so > /usr/local/etc/php/conf.d/apcu.ini

# Instalando GLPI
RUN cd /opt && wget https://github.com/glpi-project/glpi/releases/download/9.4.4/glpi-9.4.4.tgz
RUN tar -xvzf /opt/*.tgz -C /var/www/html/
RUN ls /var/www/html/glpi
RUN chown -R www-data:www-data ${glpi}

# Configurando o PHP
COPY php.ini /usr/local/etc/php/conf.d/
