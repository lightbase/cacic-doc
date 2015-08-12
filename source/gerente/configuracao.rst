====================
Configuração inicial
====================

**Configure o Apache para responder na raiz.**

+ Abra o arquivo /etc/httpd/conf/httpd.conf e altere as seguintes linhas:

``#DocumentRoot "/var/www/html"``

``DocumentRoot "/srv/cacic/web"``

----

``#<Directory "/var/www/html">``

``<Directory "/srv/cacic/web">``

``#``

``# Possible values for the Options directive are "None", "All",``

``# or any combination of:``

``#   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews``

``#``

``# Note that "MultiViews" must be named *explicitly* --- "Options All"``

``# doesn't give it to you.``

``#``

``# The Options directive is both complicated and important.  Please see``

``# http://httpd.apache.org/docs/2.2/mod/core.html#options``

``# for more information.``

``#``

``Options -Indexes FollowSymLinks``

``#``

``# AllowOverride controls what directives may be placed in .htaccess files.``

``# It can be "All", "None", or any combination of the keywords:``

``#   Options FileInfo AuthConfig Limit``

``#``

``AllowOverride All``

``#``

``# Controls who can get stuff from this server.``

``#``

``Order allow,deny``

``Allow from all``

``</Directory>``

----

+ Desabilite o SELinux: 

``setenforce Permissive``


+ Salve a alteração abrindo o arquivo /etc/selinux/config: 

``SELINUX=disabled``

----

+ Adicione as seguintes linhas no arquito /etc/sysconfig/iptables: 

``# Firewall configuration written by system-config-firewall``

``# Manual customization of this file is not recommended.``

``*filter``

``:INPUT ACCEPT [0:0]``

``:FORWARD ACCEPT [0:0]``

``:OUTPUT ACCEPT [0:0]``

``-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT``

``-A INPUT -p icmp -j ACCEPT``

``-A INPUT -i lo -j ACCEPT``


``# SSH somente nas redes autorizadas``

``-A INPUT -s 10.209.57.0/24 -m state --state NEW -m tcp -p tcp --dport 22 -j ACCEPT``

``-A INPUT -s 10.209.156.0/24 -m state --state NEW -m tcp -p tcp --dport 22 -j ACCEPT``


``# Portas HTTP e HTTPS``

``-A INPUT -p tcp -m tcp --dport 80 -j ACCEPT``

``-A INPUT -p tcp -m tcp --dport 443 -j ACCEPT``

``# Samba``

``-A INPUT -m state --state NEW -m tcp -p tcp --dport 445 -j ACCEPT``

``-A INPUT -m state --state NEW -m udp -p udp --dport 445 -j ACCEPT``

``-A INPUT -m state --state NEW -m tcp -p tcp --dport 139 -j ACCEPT``

``-A INPUT -m state --state NEW -m udp -p udp --dport 139 -j ACCEPT``

``# Libera FTP``

``-A INPUT  -p tcp -m tcp --dport 21 -j ACCEPT -m comment --comment "Allow ftp connections on port 21"``

``-A OUTPUT -p tcp -m tcp --dport 21 -j ACCEPT -m comment --comment "Allow ftp connections on port 21"``

``-A INPUT  -p tcp -m tcp --dport 20 -j ACCEPT -m comment --comment "Allow ftp connections on port 20"``

``-A OUTPUT -p tcp -m tcp --dport 20 -j ACCEPT -m comment --comment "Allow ftp connections on port 20"``

``-A INPUT  -p tcp -m tcp --sport 1024: --dport 1024: -j ACCEPT -m comment --comment "Allow passive inbound connections"``

``-A OUTPUT -p tcp -m tcp --sport 1024: --dport 1024: -j ACCEPT -m comment --comment "Allow passive inbound connections"``

``# Libera saída nas portas 80 e 443``

``-A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT``

``-A OUTPUT -p tcp -m tcp --dport 443 -j ACCEPT``

``# Liera saída para o PostgreSQL``

``-A OUTPUT -p tcp -m tcp --dport 5432 -j ACCEPT``

``-A OUTPUT -p tcp -m tcp --dport 9999 -j ACCEPT``

``# Bloqueia saída nas portas SMTP``

``-A OUTPUT -p tcp -m tcp --dport 25 -j DROP``

``-A OUTPUT -p tcp -m tcp --dport 587 -j DROP``

``# Bloqueia o resto``

``-A INPUT -j REJECT --reject-with icmp-host-prohibited``

``# Bloqueia o Forward``

``-A FORWARD -j REJECT --reject-with icmp-host-prohibited``

``COMMIT``

----

+ Carrega alterações no iptables

``service iptables restart``

Configurações do Symfony
------------------------

Como pré-requisito já deve haver um banco de dados PostgreSQL configurado para o Cacic.

+ Carregue as configurações iniciais:

cp /srv/cacic/app/config/cacic-dist-parameters.yml /srv/cacic/app/config/parameters.yml

----

+ Altere as configurações no arquivo ``/srv/cacic/app/config/parameters.yml`` 


``parameters:``
    ``database_driver: pdo_pgsql``

    ``database_host: 10.209.8.151``

    ``database_port: null``

    ``database_name: cacic``

    ``database_user: cacic``

    ``database_password: null``

    ``mailer_transport: smtp``

    ``mailer_host: 127.0.0.1``

    ``mailer_user: null``

    ``mailer_password: null``

    ``locale: pt_BR``

    ``#locale: en_US``

    ``# generate your own site secret``

    ``#secret: e410b10b0cdc810ea6bb943caa542bb42b3``

    ``database_path: null``
 
Altere o campo secret com um valor gerado no seguinte endereço: http://nux.net/secret 

Instalando o Symfony
--------------------

+ Baixe e instale os vendors:

``cd /srv/cacic``

``php composer.phar install``

+ Instale o Symfony para o Cacic:

``cd /srv/cacic``

``php app/console assets:install --symlink``

``php app/console assetic:dump --env=prod``

``php app/console assetic:dump --env=dev``

``php app/console doctrine:schema:update --force``

``php app/console doctrine:migrations:migrate``

+ Corrija as permissões:

``cd /srv/cacic``

``chown -R apache.apache``

**Terminada a instalação e configuração do Gerente Cacic 3.1, execute o navegador.**