FROM php:8.1-apache
ENV LOCALE1a="en_CA.UTF-8"
ENV LOCALE1b="en_CA:en"
ENV LOCALE2="en_US.UTF-8"
ENV LOCALE3="de_DE.UTF-8"
ENV LOCALE4="es_ES.UTF-8"
ENV LOCALE5="fr_FR.UTF-8"
ENV LOCALE6="it_IT.UTF-8"
ENV LOCALE7="nl_NL.UTF-8"
ENV LOCALE8="pl_PL.UTF-8"
ENV LOCALE9="pt_PT.UTF-8"
ENV LOCALE10="ru_RU.UTF-8"
RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf
RUN apt-get update \
#    && apt-get install -y bzip2 cron git gzip tar \
#    && apt-get install -y curl gettext libxml2 libxml2-dev locales mlocate tzdata vim php-xdebug \
    && apt-get install -y curl gettext libxml2 libxml2-dev locales mlocate tzdata vim \
    && apt-get clean -y \
#    && docker-php-ext-install intl mbstring
    && docker-php-ext-install gettext mysqli pdo pdo_mysql simplexml
#RUN apt-get update \
#    && apt-get install -y gettext \
#    && apt-get clean -y \
#    && docker-php-ext-install gettext
COPY php.ini-development /usr/local/etc/php/php.ini
RUN sed -i -e "s/# $LOCALE1a/$LOCALE1a/" /etc/locale.gen
RUN sed -i -e "s/# $LOCALE2/$LOCALE2/" /etc/locale.gen
RUN sed -i -e "s/# $LOCALE3/$LOCALE3/" /etc/locale.gen
RUN sed -i -e "s/# $LOCALE4/$LOCALE4/" /etc/locale.gen
RUN sed -i -e "s/# $LOCALE5/$LOCALE5/" /etc/locale.gen
RUN sed -i -e "s/# $LOCALE6/$LOCALE6/" /etc/locale.gen
RUN sed -i -e "s/# $LOCALE7/$LOCALE7/" /etc/locale.gen
RUN sed -i -e "s/# $LOCALE8/$LOCALE8/" /etc/locale.gen
RUN sed -i -e "s/# $LOCALE9/$LOCALE9/" /etc/locale.gen
RUN sed -i -e "s/# $LOCALE10/$LOCALE10/" /etc/locale.gen
RUN locale-gen
RUN echo "LANG=$LOCALE1a" > /etc/default/locale
ENV LANG $LOCALE1a
ENV LC_ALL $LOCALE1a
RUN a2enmod rewrite
RUN service apache2 restart
RUN mkdir -p /var/www/html/domainmod/temp
# RUN chmod -R 777 /var/www/html/domainmod/temp
RUN chmod 777 /var/www/html/domainmod/temp
EXPOSE 80
