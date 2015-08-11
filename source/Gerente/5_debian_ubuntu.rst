===============
Debian / Ubuntu
===============

Instalando os Pacotes necessários:
----------------------------------

**Instale os pacotes que você vai precisar:**
 
``apt-get -y install git postgresql apache2 php5 php5-pgsql php5-gd php5-mcrypt libapache2-mod-php5 php5-ldap php-pear php-apc subversion git openjdk-7-jre php5-intl`` 

----

**Configurando o PostgreSQL:**

O arquivo "php.ini" vem com fuso horário da Europa, logo precisamos configurá-lo para o Brasil.
 
+ Abra o arquivo "php.ini" através do comando abaixo: 

``nano /etc/php5/apache2/php.ini``

Quando o arquivo abrir digite "``CTRL + W``" para abrir a ferramenta de busca e digite "``Module Settings``" 

Você verá o comando abaixo: 

+-----------------------------------------------------------+
|[Date]                                                     |
|                                                           |
|; Defines the default timezone used by the date functions  |
|                                                           |
|; http://php.net/date.timezone                             |
+-----------------------------------------------------------+

+ Na linha imediata abaixo digite:
 
``date.timezone = America/Sao_Paulo``

Em alguns casos, pode ser que já tenha na linha ``";date.timezone ="``, neste caso complete com “America/Sao_Paulo”.

**Não esqueça de remover o “ponto e vírgula”**

**Caso já esteja atualizado, continue.**

----

Digite "``CTRL + X``" para salvar,

Confirme a alteração com "Y + Enter"

Como "root" reinicie o Apache.
 
``# /etc/init.d/apache2 restart``

Montando ambiente de desenvolvimento 
------------------------------------

+ Clone o arquivo dentro de localhost 

``# cd /srv``

``# git clone https://github.com/lightbase/cacic``

``# chown -R www-data.www-data cacic``

+ Crie um link simbólico da sua pasta web para o Apache 

``# ln -s /srv/cacic/web /var/www/cacic``

A versão do apache2 que foi publicado com o lançamento do Ubuntu 14.04 é o 2.4.7 e começando com esta versão, por razões de segurança, o novo diretório raiz para o servidor é: 

``/var/www/html``

A partir de agora, é aqui que você deve linkar o CACIC. 

``# ln -s /srv/cacic/web /var/www/html/cacic``

Caso você queira mudar este diretório, você tem que modificar (como root) a seguinte linha do arquivo /etc/apache2/sites-available/000-default.conf (sudo nano /etc/apache2/sites- available/000-default.conf): 

``DocumentRoot /var/www/html``

Para: 

``DocumentRoot /var/www``

+ Para entrar em vigor as novas mudanças, você deve reiniciar o servidor apache com o seguinte comando: 

``# sudo /etc/init.d/apache2 restart``

Crie banco de dados para o Symfony - PostgreSQL 
-----------------------------------------------

(É possível que já exista o banco de dados criado, caso isso ocorra passe para o item 5.5). 
Execute os seguintes comandos no terminal: 

``$ sudo su``

``# su - postgres``

``$ createuser cacic``

+ Responda tudo "n", conforme abaixo:

Shall the new role be a superuser? (y/n) n

Shall the new role be allowed to create databases? (y/n) n

Shall the new role be allowed to create more new roles? (y/n) n

+ Digite a linha abaixo: 

``$ createdb -O cacic cacic``
 
Liberando acesso ao banco de dados
----------------------------------
 
``# nano /etc/postgresql/9.3/main/pg_hba.conf``

+ Procure as linhas abaixo. (estão logo no início do texto) 

# PostgreSQL Client Authentication Configuration File 

# =================================================== 

# 

# Refer to the "Client Authentication" section in the PostgreSQL 

# documentation for a complete description of this file. A short 

# synopsis follows. 

# 

# This file controls: which hosts are allowed to connect, how clients 

# are authenticated, which PostgreSQL user names they can use, which 

# databases they can access. Records take one of these forms: 

# 

# local DATABASE USER METHOD [OPTIONS] 

# host DATABASE USER ADDRESS METHOD [OPTIONS] 

# hostssl DATABASE USER ADDRESS METHOD [OPTIONS] 

# hostnossl DATABASE USER ADDRESS METHOD [OPTIONS] 

+ Agora, acrescente as próximas linhas. Sem o “#”

``host cacic cacic 127.0.0.1/32 trust``

``host cacic cacic localhost trust``

Digite "CTRL + X" para sair, confirme com "y" e "enter".

+ Reiniciar o banco de dados: 

``$ /etc/init.d/postgresql restart``

Testar a conexão com o banco de dados:
--------------------------------------

Execute a linha a baixo e verifique se a mesma se encontra igual ao exemplo: 

"exit" para sair de “root” 

``$ psql -U cacic -h localhost cacic``

``psql (9.1.9)``

``SSL connection (cipher: DHE-RSA-AES256-SHA, bits: 256)`` 

``Type "help" for help.`` 

``cacic=>`` 

+ Digite "\q", depois "exit" 

$ exit 

Configurando o arquivo parameters.yml
-------------------------------------

+ Abra o arquivo "parameters.yml" conforme o comando abaixo:

``# nano /srv/cacic/app/config/parameters.yml``

+ Adicione as seguintes linhas: (este arquivo conterá somente essas linhas) 

parameters:

    database_driver: pdo_pgsql

    database_host: IP_BancoDeDados

    database_port: null

    database_name: cacic

    database_user: cacic

    database_password: null

    mailer_transport: smtp

    mailer_host: 127.0.0.1

    mailer_user: null

    mailer_password: null

    locale: pt_BR

    secret: d7c123f25645010985ca27c1015bc76797

    database_path: null


É necessário seguir um padrão de identação para que não ocorra erros na instalação do composer.phar. 

Note que as linhas do arquivo parameters.yml possuem uma tabulação de 4 espaços que deverá ser preservada. 

Digite "CTRL+X" para fechar 
Confirme com "Y + Enter" 

Executando comandos do Symfony 
------------------------------

Execute os comandos do Symfony necessários para o sistema funcionar: 

``# su - www-data``

``$ bash``

``$ cd /srv/cacic``

Caso apareça a mensagem: “*This Accont is currently not available.*” 

Acesso o arquivo passwd (digite nano /etc/passwd) 

Altere a seguinte linha linha: 

``www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin``

para: 

``www-data:x:33:33:www-data:/var/www:/bin/bash``

+ Instalação dos vendors 

``$ php composer.phar install``

Aguarde o fim da instalação (este processo pode levar alguns minutos)

Carregando os assets: (necessário haver o "java" instalado). 

Ainda com o usuário www-data execute: 

``$ php app/console doctrine:schema:update --force``

``$ php app/console assets:install --symlink``

``$ php app/console assetic:dump``

Carregando dados iniciais 
-------------------------

``# php app/console doctrine:fixtures:load``

Digite o comando "exit" e depois digite o mesmo comando "exit" novamente. 

Caso apareça a mensagem: 
*“Could not open input file: app/console”*

Finalize o terminal com "exit" 

**Terminada a instalação e configuração do Gerente Cacic 3.0, execute o navegador.**