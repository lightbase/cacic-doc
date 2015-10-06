========================================
Manual do Administrador do Super Gerente
========================================

**Informações sobre o Sistema Cacic**

O módulo integrador do Cacic, conhecido como Super Gerente, tem como objetivo consolidar as informações de hardware e software, utilizando as novas tecnologias de visualização e coleta de dados, além das interfaces de comunicação independentes baseadas em padrões abertos.

**Informações Técnicas**

Com a arquitetura definida, o órgão não é obrigado a utilizar o Cacic como software principal de inventário, mas estabelece uma sintaxe que pode ser implementada em qualquer tecnologia. Contudo, ao utilizar o módulo integrado ao Gerente, todas as etapas necessárias à coleta já estão implementadas e não resultam em custos adicionais ao órgão.
Para a administração pública, a possibilidade de haver um inventário centralizado permite o levantamento estatístico sobre as tecnologias mais utilizadas, levanta problemas referentes à concentração de utilização de software e fornece subsídios para implementar uma política de aquisição de equipamentos.

Requisitos para Implantação
^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Requisitos Mínimos**

+----------------------------------+---------------------------------------------------------------------+
|SOFTWARE                                                                                                |
+==================================+=====================================================================+
|SISTEMA OPERACIONAL:              |CentOS 6.5                                                           |
+----------------------------------+---------------------------------------------------------------------+
|WSCServer:                        |Interface de consulta SOAP: Apache + PHP + MySQL                     |
|                                  |Formato de dados de saída: XML                                       |
+----------------------------------+---------------------------------------------------------------------+
|WSCBot:                           |Plataforma tecnológica: daemon escrito na linguagem Python           |
+----------------------------------+---------------------------------------------------------------------+

**Requisitos de Infraestrutura**

A utilização do módulo Super Gerente consiste na coleta de informações consolidadas de inventário e envio para uma interface de visualização. A implementação padrão consiste na instalação de uma interface de exportação dos dados via Web Service no módulo Gerente, que é consumida pelo Agente do Super Gerente, responsável pela coleta das informações consolidadas de inventário. A coleta é então enviada para o módulo de visualização do Super Gerente, onde os dados podem ser analisados pelos usuários finais.

Uma perspectiva funcional do sistema e seus módulos.

.. image:: img/infra_supergerente.png

Instalação do Super Gerente
===========================

Módulos do Sistema.

O processo a seguir instalará todas as dependências necessárias para o correto funcionamento do módulo Super Gerente.

+ Execute o seguinte comando para ter acesso de “superusuário”

``su –``

Digite a senha do root.
 
+ Desative o SE Linux. Para isso, execute o seguinte comando:

``setenforce permissive``

**Esse comando não retornará nenhuma informação mesmo que seja executado com sucesso.**

+ Instalação de dependências.

Acesse o log de instalação das dependências constantemente para a verificação de possível erro.

``yum install gcc-c++``
``yum install zlib-devel``
``yum install opessl-devel``
``yum install postgresql-devel``
``yum install httpd``
``yum install httpd-devel``

+ Criação do diretório do projeto Super Gerente. 

Acesse o diretório ´´/usr/local/`` com o seguinte comando:

``cd /usr/local``

Crie um diretório chamado lightbase com o seguinte comando:

``mkdir lightbase``

**No diretório lightbase ficarão todos os códigos-fonte e será criado o ambiente virtual para o Super Gerente.**

Acesse o diretório lightbase:

``cd lightbase/``

+ Instalação do Phyton 3.4

Faça o download do código-fonte do Phyton 3.4 com o comando a seguir:

``wget https://www.python.org/ftp/python/3.4.1/Python-3.4.1.tar.xz``

Após a conclusão do download, descompacte o arquivo com o seguinte comando: 

``tar xf Python-3.4.1.tar.xz``

Entre no diretório onde se encontra o código-fonte:

``cd Python-3.4.1``

Execute o comando a seguir para a correta configuração do python.

``./configure --prefix=/usr/local/lightbase/ --with-threads --enable-shared LDFLAGS=-Wl, rpath=/usr/local/lightbase/lib/``

Execute os seguintes comandos:

``make``
``make install``

Abra o arquivo ld.so.conf com o seguinte comando:

``vi /etc/ld.so.conf``

Acrescente a seguinte linha:

``/usr/local/lightbase/lib``

Salve o arquivo e execute o seguinte comando:

``ldconfig``

+ Instalação do mod_wsgi modulo fundamental para a instalação do Super Gerente.

Faça o download do código fonte do mod_WSGI executando o seguinte comando:

``wget https://pypi.python.org/pypi/mod_wsgi``

Após a conclusão do download, descompacte o arquivo com o seguinte comando:

``gzip –d mod_wsgi-4.4.0.tar.gz``
``tar –xvf mod_wsgi-4.4.0.tar``

Configure com o seguinte comando:

``cd mod_wsgi-4.4.0``
``./configure  --with-python=/usr/local/lightbase/bin/python3.4``

Instale com os comandos:

``make``
``make install``

+ Instalação do virtualenv modulo responsável por criar o nosso ambiente virtual. 

Faça o download do código-fonte executando o seguinte comando:

``wget https://pypi.python.org/packages/source/v/virtualenv/virtualenv-1.11.6.tar.gz``

Após a conclusão do download, descompacte o arquivo com o seguinte comando: 

``gzip –d virtualenv-1.11.6.tar.gz``
``tar –xvf virtualenv-1.11.6.tar``

Instale com os comandos:

``cd  virtualenv-1.11.6``
``/usr/local/lightbase/bin/python3.4 setup.py install``

+ Criação do ambiente virtual 

Para criar o ambiente virtual execute o seguinte comando:

``cd /usr/local/lightbase``
``bin/virtualenv-3.4  –p  /bin/python3.4 py3env``
``cd py3env``
``mkdir src``

Ambiente virtual criado com sucesso.

+ Instalação do modulo WSCacicNeo (Interface do Super Gerente).

Acesse o ambiente virtual(py3env) e abra a pasta src com o seguinte comando:

``cd /usr/local/lightbase/py3env/src``

Faça o download do código-fonte executando o seguinte comando:

``git clone https://github.com/lightbase/WSCacicNeo.git``

Após a conclusão do download, será necessário criar um arquivo .wsgi  dentro do diretório do WSCacicNeo. Faça com o seguinte comando:

``cd WSCacicNeo/``
``vi wscacicneo.wsgi``

No documento criado insira as seguintes linhas:

``from pyramid.paster import get_app``
``application = get_app(``
``‘/usr/local/lightbase/py3env/src/WSCacicNeo/development.ini’, ’main’)``

Salve e feche o arquivo e execute o seguinte comando: 

``cp development.ini-dist  development.ini``

Execute o seguinte comando :

``cd WSCacicNeo/``
``../../bin/python3.4 setup.py develop``

Vá até a última página, veja o Modulo de configuração do seu apache, execute esse modulo e então estará apto a realizar o próximo passo.

Saia do diretorio do WSCacicNeo com o seguinte comando:

``cd ..``

Em seguida digite:

``yum install libffi-devel``

Digite:

``/../bin/pip3.4 install python-datetime``

Verifique se está no diretório src e execute o seguinte comando:

``git clone https://github.com/lightbase/liblightbase.git``

Execute o seguinte comando:

``cd liblightbase``
``../../bin/python3.4 setup.py develop ``

Saia do diretório lightbase e entre no diretório WSCacicNeo:

``cd ..``
``cd WSCacicNeo``

Execute o seguinte comando:

``../../bin/python3.4 setup.py develop``

Se em nenhum dos processos acima ocorrer erro, o WSCacicNeo(interface do Super Gerente) estará instalada com êxito.

+ Instalação Super Gerente - LBGenerator

Acesse a pasta do virtualenv e faça o download do lbgenerator:

``git clone http://git.lightbase.cc/LBGenerator.git``

Após a conclusão do download, acesse a pasta do arquivo:

``cd LBGenerator/``

	**Renomeie os arquivos lbgenerator.wsgi-dist e development.ini-dist para lbgenerator.wsgi e development.ini respectivamente.**

Abra o arquivo de configuração do wsgi:

``vim lbgenerator.wsgi``

O arquivo terá o seguinte código:

``from pyramid.paster import get_app``
``application = get_app(``
``'/home/eduardo/srv/lightbase-neo/src/LBGenerator/development.ini', 'main')``
``.``
``import lbgenerator.monitor``
``lbgenerator.monitor.start(interval=1.0)``

altere a rota do get_app para o development.ini do lbgerenator ( o que você acabou de renomear).

``'/CAMINHO/DO/LBGenerator/development.ini'``

Após configurado o arquivo wsgi, abra e configure o arquivo development.ini:

``vim development.ini``

Altere apenas a seção [alembic]:
de:
``[alembic]``
``sqlalchemy.url = postgresql://rest:rest@localhost/neolight``
``sqlalchemy.max_overflow = 0``
``sqlalchemy.pool_size = 20``
``script_location = db_versions``

para:
``[alembic]``
``sqlalchemy.url = postgresql://cacic:cacic@localhost/rest``
``sqlalchemy.max_overflow = 0``
``sqlalchemy.pool_size = 20``
``script_location = db_versions``

+ Instalação Super Gerente - WSCServer
	
Acesse a pasta do virtualenv faça o download do wscserver.

``git clone https://github.com/lightbase/WSCacicNeo.git``

Acesse a pasta do arquivo

``cd WSCServer/``

    **Renomeie o arquivo development.ini-dist para development.ini.**

Crie, caso não tenha sido criado ainda, o arquivo wscserver.wsgi:

``vim wscserver.wsgi``

Insira código a seguir:

``from pyramid.paster import get_app``
``application = get_app(``
``'/home/eduardo/srv/lightbase-neo/src/WSCServer/development.ini', 'main')``
``.``
``import wscserver.monitor``
``wscserver.monitor.start(interval=1.0)``

altere a rota do get_app para o development.ini do wscserver ( o que você acabou de renomear).

``'/CAMINHO/DO/WSCServer/development.ini'``

Abra e configure o arquivo development.ini:

``vim development.ini``

Altere a seção [alembic] para:

``[alembic]``
``sqlalchemy.url = postgresql://cacic:cacic@localhost/cacic``
``sqlalchemy.max_overflow = 0``
``sqlalchemy.pool_size = 20``
``script_location = db_versions``
``5.0 Instalação Super Gerente - LBBulk``

Acesse a pasta do virtualenv e faça o download do lbbulk.

``git clone https://github.com/lightbase/LBBulk.git``

Acesse a pasta do arquivo:

``cd LBBulk/``

	**Renomeie os arquivos lbbulk.wsgi-dist e development.ini-dist para lbbulk.wsgi e development.ini respectivamente.**

Abra o arquivo de configuração do wsgi:

``vim lbbulk.wsgi``

O arquivo terá o seguinte código:

``from pyramid.paster import get_app, setup_logging``
``ini_path = '/srv/lightbase/LBBulk/development.ini'``
``#ini_path = '/srv/lightbase/LBBulk/production.ini'``
``.``
``setup_logging(ini_path)``
``application = get_app(ini_path, 'main')``

Altere a rota do ini_path para o development.ini do lbbulk (o que acabou de ser renomeado).

``'/CAMINHO/DO/LBBulk/development.ini'``

Abra e configure o arquivo development.ini:

``vim development.ini``

Altere a lightbase_url:

``lightbase_url = http://127.0.0.1/lbgenerator``

+ Instalação e configuração do Postgresql

Para a instalação do Postgresql no CentOS, verifique a seguinte URL	

``https://wiki.postgresql.org/wiki/YUM_Installation``

Após executar os passos no tutorial de instalação acima, será criado um superusuário chamado cacic no postgresql. Com esse mesmo superusuário serão criadas duas bases, uma chamada rest e a outra cacic. Estas são as bases que os módulos LBGenerator e WSCServer usarão para armazenar seus dados. 

Crie o superusuário e as bases.

Para acessar o Postgresql digite: 

``su – postgres``

**OBS: isso ira alterar o usuario do sistema que atualmente é o root e irar se tornar postgres**

Acesse o terminal postgresq digitando o seguinte comando:

``psql``

Execute os seguintes comandos:

``CREATE USE cacic SUPERUSER INHERIT CREATEDB CREATEROLE;``
``ALTER USER cacic PASSWORD 'cacic';``

Abra o arquivo pg_hba.cong com o seguinte comando:

``cd /var/lib/pgconf/pg_hba.conf``

Adicione a seguinte linha:

``Localhost         all     cacic     127.0.0.1  trust``

Salve o arquivo e reinicie o postgressql:

``/etc/init.d/posgresql restart``

Acesse o terminal do postgres com o usuário criado da seguinte forma:

``psql –H localhost –U cacic –W``

Insira a senha “cacic”, e execute os seguintes comandos:

``CREATE DATABASE cacic;``
``CREATE DATABASE rest;``

Reinicie o apache com o seguinte comando:

``/etc/init.d/httpd restart``

**Caso não retorne erro em nenhuma das instalações, o sistema estará configurado de maneira correta.**

Para verificação de qualquer erro, acesse o arquivo error.log com o seguinte comando:

``less /var/log/httpd/error.log``

+ Módulo de configuração do apache (httpd)

Para configurar o apache(httpd), crie ou acesse o arquivo:

``sudo vi /etc/httpd/conf.d/lightbase.conf``

Insira o seguinte código, de acordo com sua configuração:

``LoadModule wsgi_module /usr/lib64/httpd/modules/mod_wsgi.so``
``WSGISocketPrefix /var/run/wsgi``
``ServerAdmin admin@lightbase.com.br``
``WSGIApplicationGroup %{GLOBAL}``
``WSGIPassAuthorization On``

Configure o WSCacicNeo no httpd, inserindo após o código a cima, as seguintes linhas de comando:

``WSGIDaemonProcess wscacicneo threads=8 python-path=/usr/local/lightbase/py3env/lib/python3.4/site-packages``
``WSGIScriptAlias /wscacicneo /usr/local/lightbase/py3env/src/WSCacicNeo/wscacicneo.wsgi``
``<Directory /usr/local/lightbase/py3env>``
``WSGIProcessGroup wscacicneo``
``Order allow,deny``
``Allow from all``
``</Directory>``

Configure o WSCServer, adicione as seguintes linhas ao lightbase.conf:

``WSGIDaemonProcess wscserver threads=8 python-path=/usr/local/lightbase/py3env/lib/python3.4/site-packages``
``WSGIScriptAlias /wscserver /usr/local/lightbase/py3env/src/WSCServer/wscserver.wsgi``
``<Directory /usr/local/lightbase/py3env>``
``WSGIProcessGroup wscserver``
``Order allow,deny``
``Allow from all``
``</Directory>``

Configure o LBBulk, adicione as seguintes linhas ao lightbase.conf:

``WSGIDaemonProcess lbbulk threads=8 python-path=/usr/local/lightbase/py3env/lib/python3.4/site-packages``
``WSGIScriptAlias /lbbulk /usr/local/lightbase/py3env/src/LBBulk/LBBulk.wsgi``
``<Directory /usr/local/lightbase/py3env>``
``WSGIProcessGroup lbbulk``
``Order allow,deny``
``Allow from all``
``</Directory>``

