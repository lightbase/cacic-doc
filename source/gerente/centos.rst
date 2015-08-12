========
CentOS 6
========

**Preparação inicial.**

+ Instale o software de suporte:
 
``cd /tmp``

``yum install wget java-1.8.0-openjdk``


+ Configure mirror da globo.com para software SCL                                                    

``echo "``

``[SCL]``                                                                                    

``name=CentOS-\$releasever - SCL``                                                                    

``baseurl=http://mirror.globo.com/centos/6/SCL/\$basearch/``                                           

``gpgcheck=1``                                                                                        

``Priority=1``                                                                                        

``enabled=1``                                                                                         

``gpgkey=http://mirror.globo.com/centos/RPM-GPG-KEY-CentOS-Testing-6" >``                              

``/etc/yum.repos.d/CentOS-SCL-globo.repo``                                                             

``rpm --import http://mirror.globo.com/centos/RPM-GPG-KEY-CentOS-Testing-6``                          

+ PHP                                                                                                  

``yum install php54 php54-php php54-php-xml php54-php-pdo php54-php-gd php54-php-mcrypt  php54-php-pgsql
php54-php-intl php54-php-pecl-apc``                                                                     

+ Habilite nova versão do PHP                                                                           

``scl enable php54 "php -v"``

``source /opt/rh/php54/enable``

``rm /etc/httpd/conf.d/php.conf``

``/usr/sbin/apachectl -t``

``/etc/init.d/httpd restart``

+ Instale o  mcrypt

``cd /tmp``
``wget https://www.softwarecollections.org/repos/remi/php54more/epel-6-x86_64/php54-php-mcrypt-5.4.16-3.el6.x86_64.rpm``


+ Corrija o fuso horário do php:

``vi /opt/rh/php54/root/etc/php.ini``

``date.timezone = America/Sao_Paulo``

``Ajustes de parâmetros``

``max_execution_time = 300``

``memory_limit = 512M``


+ Baixe o Código do Gerente

``cd /srv``

``wget https://github.com/lightbase/cacic/archive/v3.1.14.tar.gz``

``tar -xzvf v3.1.14.tar.gz``

``ln -s cacic-3.1.14 cacic``

 **Obs.:** Para escolher outra release acesse a página do Cacic e veja a última disponível: ``https://github.com/lightbase/cacic/releases``