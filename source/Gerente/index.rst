.. Cacic documentation master file, created by
   sphinx-quickstart on Fri Aug  7 17:07:34 2015.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Cacic's documentation!
=================================

===============
O Sistema Cacic
===============

Defini��o do Sistema
====================
O sistema CACIC - Configurador Autom�tico e Coletor de Informa��es Computacionais trabalha com o uso de software para as plataformas MS-Windows e GNU/Linux e funciona essencialmente a partir do trabalho de m�dulos agentes, onde utiliza como base conceitual a metodologia MaSE (Multi-agentCACIC � Configurador Autom�tico e Coletor de Informa��es Computacionais Software Engineering). Na plataforma MS-Windows, os agentes s�o programas compilados e n�o criam depend�ncias ao seu funcionamento. Dessa forma, qualquer empresa/�rg�o que queira utilizar o CACIC n�o necessitar� de softwares adicionais para a implanta��o do Sistema. 

O Cacic � capaz de fornecer um diagn�stico preciso do parque computacional e disponibilizar informa��es como o n�mero de equipamentos e sua distribui��o nos mais diversos �rg�os, os tipos de softwares utilizados e licenciados, configura��es de hardware, entre outras. Tamb�m pode fornecer informa��es patrimoniais e a localiza��o f�sica dos equipamentos, ampliando o controle do parque computacional e a seguran�a na rede.

===========================
Requisitos para Implanta��o
===========================

Requisitos Minimos
==================


+----------------------------------+---------------------------------------------------------------------+
|HARDWARE                                                                                                |
+==================================+=====================================================================+
|CPU:                              |Pentium/AMD quadcore (ou superior)                                   |
+----------------------------------+---------------------------------------------------------------------+
|Mem�ria RAM:                      |4 Gbytes                                                             |
+----------------------------------+---------------------------------------------------------------------+
|Disco r�gido:                     |100 Gbytes                                                           |
+----------------------------------+---------------------------------------------------------------------+
|Interface de rede                 |                                                                     |
+----------------------------------+---------------------------------------------------------------------+

+----------------------------------+---------------------------------------------------------------------+
|SOFTWARE                                                                                                |
+=============================+==========================================================================+
|SISTEMA OPERACIONAL:         |Sistema desenvolvido para qualquer distribui��o GNU/Linux;)               |
+-----------------------------+--------------------------------------------------------------------------+
|Servidor Web:                |PHP5: 5.4.13 ou superior                                                  |
+-----------------------------+--------------------------------------------------------------------------+
|Servidor de banco de dados:  |PostgreSQL                                                                |
+-----------------------------+--------------------------------------------------------------------------+
|PHP:                         |- Criptografia com MCrypt (php-MCrypt)                                    |
|                             |- PHP com suporte a troca de arquivos por FTP. (php-FTP)                  |
|                             |- PHP com suporte a conex�o a servi�o de diret�rios padr�o LDAP.(php-LDAP)|
|                             |- PHP com suporte a imagens com GD (php-GD)                               |
|                             |- PHP intl                                                                |
|                             |- Biblioteca de criptografia SSL                                          |
+-----------------------------+--------------------------------------------------------------------------+
|APACHE:                      |- Mem�ria para execu��o de programas PHP:--- 512MB (MINIMO)               |
+-----------------------------+--------------------------------------------------------------------------+


Para o Agente Linux s�o necess�rios o ambiente de desenvolvimento em C;
Maiores informa��es podem ser obtidas nos s�tios dos respectivos fabricantes: http://httpd.apache.org/; http://www.mysql.com/; http://www.php.net/; http://sourceforge.net; http://www.proftpd.org/
Pr� condi��o: � necess�rio estar conectado a internet, e banco de dados PostgreSQL instalado.

