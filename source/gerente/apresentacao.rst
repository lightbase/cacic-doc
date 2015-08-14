===============
O Sistema Cacic
===============

**Definição do Sistema**

O sistema CACIC - Configurador Automático e Coletor de Informações Computacionais trabalha com o uso de software para as plataformas MS-Windows e GNU/Linux e funciona essencialmente a partir do trabalho de módulos agentes, onde utiliza como base conceitual a metodologia MaSE (Multi-agentCACIC - Configurador Automático e Coletor de informações Computacionais Software Engineering). Na plataforma MS-Windows, os agentes são programas compilados e não criam dependências ao seu funcionamento. Dessa forma, qualquer empresa/órgão que queira utilizar o CACIC não necessitará de softwares adicionais para a implantação do Sistema. 


O Cacic é capaz de fornecer um diagnósco preciso do parque computacional e disponibilizar informações como o número de equipamentos e sua distribuição nos mais diversos órgãos, os tipos de softwares utilizados e licenciados, configurações de hardware, entre outras. Também pode fornecer informações patrimoniais e a localização física dos equipamentos, ampliando o controle do parque computacional e a segurança na rede.

Requisitos para Implantação
^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Requisitos Mínimos**

+----------------------------------+---------------------------------------------------------------------+
|HARDWARE                                                                                                |
+==================================+=====================================================================+
|CPU:                              |Pentium/AMD quadcore (ou superior)                                   |
+----------------------------------+---------------------------------------------------------------------+
|Memória RAM:                      |4 Gbytes                                                             |
+----------------------------------+---------------------------------------------------------------------+
|Disco rígido:                     |100 Gbytes                                                           |
+----------------------------------+---------------------------------------------------------------------+
|Interface de rede                 |                                                                     |
+----------------------------------+---------------------------------------------------------------------+

+----------------------------------+---------------------------------------------------------------------+
|SOFTWARE                                                                                                |
+=============================+==========================================================================+
|SISTEMA OPERACIONAL:         |Sistema desenvolvido para qualquer distribuição GNU/Linux;)               |
+-----------------------------+--------------------------------------------------------------------------+
|Servidor Web:                |PHP5: 5.4.13 ou superior                                                  |
+-----------------------------+--------------------------------------------------------------------------+
|Servidor de banco de dados:  |PostgreSQL                                                                |
+-----------------------------+--------------------------------------------------------------------------+
|PHP:                         |- Criptografia com MCrypt (php-MCrypt)                                    |
|                             |- PHP com suporte a troca de arquivos por FTP. (php-FTP)                  |
|                             |- PHP com suporte a conexão a serviço de diretórios padrão LDAP.(php-LDAP)|
|                             |- PHP com suporte a imagens com GD (php-GD)                               |
|                             |- PHP intl                                                                |
|                             |- Biblioteca de criptografia SSL                                          |
+-----------------------------+--------------------------------------------------------------------------+
|APACHE:                      |- Memória para execução de programas PHP:--- 512MB (MINIMO)               |
+-----------------------------+--------------------------------------------------------------------------+

Para o Agente Linux são necessários o ambiente de desenvolvimento em C;
Maiores informações podem ser obtidas nos sítios dos respectivos fabricantes: http://httpd.apache.org/; http://www.mysql.com/; http://www.php.net/; http://sourceforge.net; http://www.proftpd.org/
Pré condição: É necessário estar conectado a internet, e banco de dados PostgreSQL instalado.

Instalação Manual
^^^^^^^^^^^^^^^^^

Este roteiro irá orientá-lo como fazer uma NOVA instalação do Gerente Cacic 3.1 em máquinas com Sistema Operacional Linux. 

A instalação ocorre basicamente por linhas de comando através do Terminal, para tanto, acesse o Painel Inicial (Launcher) que fica localizado no canto superior esquerdo de sua tela. 

Após aparecer a opção de busca digite “``Terminal``” e pressione a tecla "``Enter``". Agora seguiremos com os comandos dentro do Terminal. 

Caso não o encontre utilize as teclas de atalho “``CTRL + ALT + T``”. 

**Utilizando o Terminal**

Observação sobre o uso do terminal: 

Dentro do terminal o cursor ficará sempre depois de "``$``" ou "``#``". 

Sempre que o comando a ser copiado for precedido por "``$``", significa que este é um comando de usuário normal; 

Sempre que o comando a ser copiado for precedido por "``#``", significa que este é um comando de usuário “``root``”. 

Caso o comando a ser copiado não seja precedido por "``$``" nem por "``#``", significa que este comando pode ser executado sem restrições. 

Para acessar como “``root``” digite "``sudo su``". 

Foi utilizado para este tutorial o “Terminal” em idioma inglês, então as confirmações apresentadas aqui estão em (Yes/Y ou No/N), caso seu sistema esteja em português confirme com (Sim/S ou Não/N). 

Siga a instalação passo a passo. Caso algum procedimento venha a falhar, não desconsidere pois pode ocasionar outros erros. Corrija-os antes de prosseguir com a instalação.
