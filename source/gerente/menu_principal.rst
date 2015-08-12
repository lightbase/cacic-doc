=====================
Utilização do Sistema
=====================

**Configuração Inicial**

 Para que o sistema efetivamente comece funcionar, é preciso que seja realizada a primeira coleta, para isso é necessário cadastrar pelo menos uma Sub-rede e habilitar os módulos de coleta.

----

**Cadastro de Sub-redes**


 Cada registro de sub-rede contém detalhes específicos que determinam a abrangência, servidores de aplicação e atualização de versões e informam sobre as coletas associadas.

+ Acesse o Menu Administração → Cadastros → Sub-redes 

.. image:: img/cadastro_subrede.png

 Clique em “Adicionar Subrede” preencha os dados e clique em “Salvar Dados”.

----

**Habilitando módulos**

 Possibilita a configuração dos vários módulos do CACIC.

+ Acesse o Menu Administração → Configurar Coletas → Configurar Módulos. 

 Selecione o módulo que deseja habilitar. 

.. image:: img/habilitar_mod.png

 Marque as sub-redes e em seguida clique em “Salvar Dados”. 

.. image:: img/habilitar_mod1.png

 Com isso, o sistema está pronto para realizar as coletas.

----

**Atualizando Sub-redes**

+ Acesse o Menu Administração → Configurar Coletas → Atualização de Sub-redes

 Mais ao final da página vá até Sub-redes Cadastradas conforme exemplo abaixo.

.. image:: img/atualizar_subrede.png

 Selecione a(s) sub-rede(s) que deseja atualizar e logo em seguida clique em “Executar Atualizações”. 

=====================================
Configuração de instalação adicional.
=====================================

**Importar dados do Cacic 2.6**

 Esta configuração, permite migrar todos os dados da versão 2.6 para a atual.

+ Acesse o Menu Administração → Importar de 2.6 

 Adicione o arquivo .zip para a importação dos dados, gerado pelo Gerente Cacic 2.6 e logo em seguida clique em “Salvar Dados”.

.. image:: img/importar_dados.png

=============================
A tela principal do Cacic 3.1
=============================

 A tela principal do Cacic (home), é composta por elementos dinâmicos que facilitam a visualização das atividades mais importantes para o gerenciamento do parque computacional. Sua estrutura se divide da seguinte forma: Menu Principal; Barra de título e configurações rápidas do sistema; Barra de atalho para o Cacic e para o Software Cocar; Estatísticas do Sistema; Atalhos; Mensagem de boas vindas ao usuário; Relatório simplificado de Computadores monitorados por sistema operacional. Detalharemos toda estrutura abaixo.

===================
Menu Principal.
===================

**Conhecendo os menus do Cacic 3.1.**

 Os menus do software Cacic são organizados tendo como base os perfis de grupos de usuários.

.. image:: img/menu_principal.png

+ **Grupo de usuários “Administradores”:** São os usuários previamente definidos que possuem acesso irrestrito ao sistema.

+ **Grupo de usuários “Gestores”:** Possuem acesso de leitura em todas as opções. Manutenção de tabelas e acesso a todas as informações referentes à Localização. 

+ **Grupo de usuários “Técnicos”:** Acesso técnico. Será permitido acessar configurações de rede e relatórios de Patrimônio e Hardware. Administração:

----

**Administração:**

+ **Configurar Coletas:** Menu com configurações básicas para executar coletas dos agentes.

 - **Upload de Agentes:** Ferramenta para envio ao servidor de novos binários dos Agentes. Selecione os arquivos referentes à versão do sistema e clique em “Enviar Dados”. Os arquivos devem estar em formato “.zip” ou “.tar.gz”.

.. image:: img/upload_agentes.png

 - **Deploy de Software:** Ferramenta para envio de binários diversos ao sistema. Estes binários não necessariamente são do Cacic. Basta selecionar o arquivo desejado e clicar em “Enviar Dados”.

 - **Atualização de Subrede:** Ferramenta para controle dos binários nas diversas redes da organização. Através deste menu, é possível verificar se alguma sub-rede possui seu binário desatualizado ou inexistente. Para o uso, selecione as redes que pretende atualizar e clique em “Executar Atualização”.

 - **Configurar Módulos:** O Software Cacic permite que as modificações sejam feitas de forma controlada, selecionando em quais redes os binários devem agir. Para o uso, primeiramente, selecione qual o módulo pretende atualizar, logo após, informe em qual(is) subrede(s) será atualizado e clique em “Salvar Dados” para confirmar sua atualização. Mostrado no item “Habilitando módulos”

+ **Logs:** Ferramenta do sistema que disponibiliza diversas informações sobre o comportamento e atividades do sistema.

 - **Acessos:** O Log de Acesso informa os usuários que tiveram acesso ao sistema em determinado período. Para visualizar o log primeiramente escolha o período inicial e final e o local (os usuários podem ser criados com locais primários) e clique em “Filtrar”, na tela seguinte será apresentado o relatório solicitado.

 - **Atividades:** O Log de Atividades informa quais atividades foram realizadas no sistema em determinado período. Para visualizar o log primeiramente escolha o período inicial e final e o local (os usuários podem ser criados com locais primários) e clique em “Filtrar”. Na tela seguinte será apresentado o relatório solicitado.

 - **Insucessos Instalação:** Este log informa as instalações dos agentes que não foram realizadas com sucesso. Para sua visualização, simplesmente escolha o período e clique em “Filtrar”.

+ **Cadastros:** Ferramenta do sistema para inserção e edição de novos itens.

 - **Locais:** O sistema Cacic se baseia na localização física em que o componente se encontra. Para isso, se faz necessário inicialmente, o cadastro do local onde este computador se encontra e depois as sub-redes que este local possui. Ao navegar pelo menu e clicar em “Locais”, será apresentada uma tela com os locais já cadastrados, caso já exista algum. Para adicionar um novo local, clique em “Adicionar Local”. Na tela seguinte serão apresentadas três abas onde somente a primeira deve ser preenchida (Dados do local). Coloque o nome e a sigla do novo local e caso seja necessário, uma observação e após clique em “Salvar Dados”.

 - **Servidores de Autenticação:** Neste módulo deverão ser cadastrados todos os servidores de autenticação para uso nas aberturas de sessões de suporte remoto seguro. Ao navegar pelo menu e clicar em “Servidores Autenticação”, será apresentada uma tela com os servidores já cadastrados, caso já exista algum. Para adicionar um novo, clique em “Adicionar Servidor”. Na tela seguinte serão apresentadas quatro abas. Preencha os dados necessários nas abas e na última selecione em quais redes este servidor estará ativo. Ao finalizar clique em “Salvar Dados”.

 - **Sub-redes:** Para o software Cacic, os locais possuem suas sub-redes. Após o cadastro anterior dos locais, este módulo cadastra as sub-redes deste local. Ao navegar pelo menu e clicar em “Sub-Redes”, será apresentada uma tela com as sub-redes já cadastradas, caso já exista alguma. Para adicionar uma nova sub-rede, clique em “Adicionar Subrede”. Na tela que se abre, preencha os campos com os dados relativos a nova sub-rede. O local é um dos já criados anteriormente (caso não tenha nenhum local criado, faça fazer em “Cadastros → Locais”) Em servido de autenticação, escolha um previamente cadastrado (caso não tenha nenhum servidor cadastrado, faça em “Cadastros → Servidores Autenticação”). Em “Subrede”, informe o endereço IP da rede que deseja cadastrar e informe logo após a máscara de rede. Informe o endereço da aplicação, do servidor de upload dos Agentes e método de download (FTP ou HTTP). Caso o upload dos Agentes seja realizado pelo método FTP, informe usuário e senha para acesso. Selecione ao final da página se todos os módulos estarão habilitados para esta rede e clique em “Salvar Dados”.

 - **Computadores e Subredes:** Este módulo agrupa todas as máquinas que por alguma razão tiveram sua sub-rede identificada de forma diferente da prevista. Caso uma determinada máquina esteja em uma sub-rede “X” mas apresente um endereço IP diferente da rede, esta máquina será apresentada neste módulo, onde é possível realizar manualmente, a correta alocação da mesma. Ao navegar pelo menu e clicar em “Computadores e Subredes”, será apresentada uma tela com todas as máquinas com divergência de sub-rede, caso exista alguma. Para realizar a alocação das mesmas, selecione as máquinas desejadas e clique em “Executar Atualização”.

+ **Usuário:** Este módulo é o responsável pelo cadastro das pessoas que utilização o Sistema Cacic. Aqui é possível realizar o cadastro de um usuário individual ou de um grupo de usuários com acessos diferenciados.

 - **Cadastro de Usuários:** Neste módulo é possível visualizar um usuário já cadastrado no sistema, editá-lo e também cadastrar um novo. Ao navegar pelo menu e clicar em “Cadastro de Usuários”, será apresentada uma tela com os usuários já cadastrados, caso já exista algum. Para adicionar um novo usuário, clique em “Adicionar Usuário”. Na tela seguinte, preencha os campos com os dados sobre o usuário que deseja cadastrar e clique em “Salvar Dados”.

 - **Cadastro de Grupos de Usuários:** Módulo para cadastro de grupo de usuários com permissões de acesso diferenciadas. Neste módulo é possível visualizar um grupo já cadastrado no sistema, editá-lo e também cadastrar um novo. Ao navegar pelo menu e clicar em “Grupo de Usuários”, será apresentada uma tela com os grupos já cadastrados, caso já exista algum. Para adicionar um novo grupo, clique em “Adicionar Grupo de Usuários”. Na tela seguinte, preencha os campos com os dados sobre o grupo que deseja cadastrar e clique em “Salvar Dados”.

+ **Patrimônio:** Controles para Patrimônio.

 - **Unidades Organizacionais:** Neste módulo deverão ser cadastradas todas as unidades organizacionais do sistema - Entidades, Linhas de negócio e Órgãos. 

 - **Tipos de Unidade Organizacional:** Neste módulo deverão ser cadastrados os tipos de Unidades Organizacionais 

+ **Forçar Coletas:** Os Agentes Cacic realizam nas máquinas na qual estão instalados em períodos programados no Gerente. Estes agentes verificam todos os itens de hardware e software na máquina é enviam para o Gerente. Caso o resultado da coleta atual seja diferente da anterior, os dados são enviados, caso contrário, não. A função “Forçar Coletas” permite informar aos agentes que enviem as informações ao gerente mesmo que as mesmas sejam iguais à coleta anterior. Esta ação não ocorre instantaneamente ao ser solicitada, mas agenda para que na próxima coleta, os dados sejam enviados indiferente de serem iguais ou não.

 - **Forçar coleta computador:** Permite que se escolha uma máquina, através de seu endereço IP, MAC Adress ou nome de registro e depois se solicite a coleta forçada. Para sua execução, selecione uma forma de pesquisa, informe o dado  e clique em “Buscar”, após isso será gerado o resultado da busca com a(s) máquina(s) escolhidas, clique em “Coletar” para finalizar.

 - **Forçar coleta subrede:** Esta opção permite escolher uma ou diversas sub-redes para forçar a coleta. Para sua execução, selecione qual(is) rede(s) devem ser forçadas e clique em “Forçar Coleta”.

+ **Versões Agentes:** Este módulo exibe as versões dos agentes que estão comunicando com o Gerente. É mostrado como período, o histórico total e últimos 30 dias.

----

**Manutenção:**

+ **Cadastros:** Controle de módulos relativos à Sistemas Operacionais e dispositivos.

 - **Tipos de SO:** Módulo para cadastro e edição dos tipos de sistemas operacionais (Windows ou Linux). Estes devem ser os tipos de sistemas na qual os binários devem ser carregados ao sistema no menu “Administração → Configurar Colatas → Uploads de Agentes”.

 - **Sistemas Operacionais:** Mesmo menu acessado por “ Administração → Cadastros → Sistemas Operacionais”, e explicado no item 4.3.2.

 - **Aplicativos Monitorados:** No sistema Cacic é possível criar um filtro para monitoramento de determinados softwares. Ao navegar pelo menu e clicar em “Aplicativos Monitorados”, será apresentada uma tela com os aplicativos já cadastrados, caso já exista algum. Para adicionar um novo aplicativo, clique em “Adicionar Aplicativo”. Na tela seguinte, preencha os campos com os dados sobre o aplicativo que deseja monitorar e clique em “Salvar Dados”.

 - **Dispositivos USB:** Mesmo menu acessado por “ Administração → Cadastros → Dispositivos USB”, e explicado no item 4.3.2.

 - **Dispositivos 3G:** O sistema Cacic, através dos seus Agentes, localiza em todas as máquinas monitoradas a presença de dispositivos para conexão 3G e os aloca neste módulo, onde é possível visualizar um dispositivo, editá-lo e também cadastrar um novo. Ao navegar pelo menu e clicar em “Dispositivos 3G”, será apresentada uma tela com os dispositivos já cadastrados, caso já exista algum. Para adicionar um novo dispositivo, clique em “Adicionar 3G”. Na tela seguinte, preencha os campos com os dados sobre o dispositivo que deseja cadastrar e clique em “Salvar Dados”.

+ **Classificação de Software:** O Software Cacic através de seus Agentes, realiza uma varredura completa nos computadores que estão instalados e retornam ao Gerente as mais diversas informações sobre os softwares instalados e sobre os hardwares presentes no dispositivo. Neste módulo, é possível definir e classificar todos os tipos de softwares encontrados.

 - **Tipo de Software:** Aqui é possível criar, visualizar e editar quais são os tipos de softwares encontrados nos computadores pelos Agentes do Cacic. Alguns exemplos são: Softwares Licenciados; Softwares Livres; Jogos e Similares; Software Suspeito, dentre outros. Ao navegar pelo menu e clicar em “Tipos de Softwares”, será apresentada uma tela com os tipos de softwares já cadastrados, caso já exista algum. Para adicionar um novo dispositivo, clique em “Software”. Na tela seguinte, preencha os campos com os dados sobre o software que deseja cadastrar e clique em “Salvar Dados”.

 - **Selecionar Tipo:** A classificação de software pode ser feita individual ou selecionando um grupo de softwares.

  - **Em grupo:** Nesta ferramenta será apresentada uma lista com todos os softwares, divididos por páginas conforme a quantidade encontrada, onde o usuário fará a classificação de vários softwares ao mesmo tempo conforme os tipos possíveis. 

  - **Um por um:** Permite a classificação de softwares inventariados conforme tipos possíveis um por um. Nesta ferramenta será apresentada uma lista com todos os softwares, divididos por páginas conforme a quantidade encontrada, mas diferente da classificação em grupo, aqui é necessário abrir cada um dos itens para efetuar a classificação. 

+ **Controle de Licenças:** Módulo para controle das licenças.

 - **Tipos de Licenças:** Nesta ferramenta devem ser cadastradas quais os tipos de licença encontrados pelo sistema. Ao navegar pelo menu e clicar em “Tipos de Licenças”, será apresentada uma tela com os tipos de licenças já cadastradas, caso já exista alguma. Para adicionar um novo tipo de licença, clique em “Adicionar Licença”. Na tela seguinte, preencha os campos com os dados sobre a licença que deseja cadastrar e clique em “Salvar Dados”.

 - **Processo de Aquisição:** Neste módulo podem ser controlados os processos de aquisição de software do órgão. Ao navegar pelo menu e clicar em “Controle de Aquisição”, será apresentada uma tela com as aquisições já cadastradas, caso já exista alguma. Para adicionar uma nova aquisição, clique em “Adicionar Aquisição”. Na tela seguinte, preencha os campos com os dados sobre o software que deseja cadastrar e clique em “Salvar Dados”.

 - **Softwares Adquiridos:** Neste módulo são apresentados os processos de software cadastrados, sendo possível exibir, editar ou cadastrar processos.

 - **Software por Estação:** Este módulo permite vincular softwares e estações de trabalho.

+ **Localização:** Esta função permite a tradução, de forma rápida, dos termos utilizados no sistema..

----

+ **Computadores:**

 - **Navegar:** Módulo que abre em formato de “raiz” todas as máquinas coletadas pelo sistema. Esta funcionalidade é organizada por locais – sub-redes – computadores. Para sua execução basta ir clicando sobre as setas nas linhas que vão se abrindo.

 - **Consultar:** Este módulo possibilita a busca de uma unidade computacional específica. Para execução selecione o tipo de consulta que deseja fazer e informe o dado escolhido. Após, clique em “Consultar”. O resultado será gerado logo abaixo da pesquisa. Para abrir a máquina escolhida, clique no botão da lupa ao final da coluna.

 - **Busca Avançada:** Este módulo possibilita a busca de uma unidade computacional específica. Para execução selecione o tipo de consulta que deseja fazer e informe o dado escolhido. Este módulo possibilita mais opções de busca. Após, clique em “Consultar”. O resultado será gerado logo abaixo da pesquisa. Para abrir a máquina escolhida, clique no botão da lupa ao final da coluna.

----

**Relatórios:**

+ **Softwares:**

 - **Relatório de Software:** Este relatório exibe os relatórios de software cadastrados nos computadores das redes selecionadas. É possível determinar quais softwares serão exibidos no relatório, os sistemas operacionais e a abrangência das redes . 

 - **Cadastro de Relatórios:** Essa página mostra os relatórios de software cadastrados no sistema, agrupando componentes de software na mesma tela. É possível visualizar os relatórios já cadastrados e também gerar um novo.

 - **Softwares Inventariados:** Este relatório exibe os softwares inventariados nos computadores das redes selecionadas. É possível determinar quais softwares serão exibidos no relatório, os sistemas operacionais e a abrangência das redes.

 - **Controle de Licenças:** Possibilita o cadastro dos tipos de licença, processo de aquisições, softwares adquiridos e softwares inventariados vinculados às estações de trabalho

 - **Tipos de Softwares:** Este relatório exibe as máquinas em que os Softwares estão sendo utilizados. É possível determinar quais Tipos de Softwares serão exibidos no relatório. 

+ **Computadores:**

 - **Faturamento:** Relatório que apresenta todas as máquinas coletadas pelo sistema. Este em sua pesquisa, utiliza um filtro que agrupa as máquinas pelo seu MAC Adress, não gerando valores duplicados. Na consulta deste relatório pode-se escolher o período e as sub-redes que serão pesquisadas.

 - **Total de Computadores:** Relatório que apresenta todas as máquinas coletadas pelo sistema. Na consulta deste relatório pode-se escolher o período e as sub-redes que serão pesquisadas.

 - **Relatório para Ateste:** Este relatório gera ao usuário informação consolidada sobre sub-redes e quantidade de máquinas em cada uma para o ateste. Para execução selecione as sub-redes que deseja atestar, preencha os dados necessários e clique em “Atestar”.

 - **Computadores Inativos:** Relatório que apresenta todas as máquinas que não se comunicam com o sistema por mais que o tempo pré-definido.

+ **Hardware:**

 - **Classes WMI:** Relatório das classes WMI do Windows.

 - **WMI Sem Coleta:** Este relatório permite que o usuário gere relatórios sobre máquinas que não tiveram classes WMI coletadas. Para execução selecione a classe que deseja gerar o relatório, podendo ser um ou mais, e clique em “Gerar Relatório”. O resultado será gerado em uma próxima tela.

 - **Sistemas Operacionais:** Este relatório permite que o usuário gere relatórios personalizados sobre sistemas operacionais. Para execução selecione o sistema que deseja gerar o relatório, podendo ser um ou mais, e clique em “Gerar Relatório”. O resultado será gerado em uma próxima tela. É possível também gerar um arquivo “.csv”.

 - **Usuário Logado:** Este Relatório informa qual o usuário logado no sistema no momento em que a última coleta foi realizada. O log não representa o usuário logado no momento da coleta, pois sua atuação não é em tempo real. Para sua visualização, escolha o período desejado e caso tenha interesse, utilize um ou mais filtros disponíveis. Após, clique em “Gerar Relatório”.

 - **WMI Dinâmico:** Este relatório permite que o usuário gere relatórios personalizados sobre todas as classes WMI disponíveis. Para execução selecione a classe que deseja gerar o relatório, podendo ser um ou mais, e clique em “Gerar Relatório”. O resultado será gerado em uma próxima tela.

----

**Downloads:**

 Ferramenta do sistema Cacic onde é possível realizar um download dos arquivos binários. Navegue pelas pastas e ao efetuar um duplo clique com o botão esquerdo do mouse sobre o aquivo, o sistema solicitará a permissão para baixar o arquivo solicitado.

----

**Comunidade CACIC:**

 Ferramentados sistema Cacic que leva o usuário a uma página da web onde o mesmo poderá encontrar todas as informações pertinentes à utilização e configuração do sistema.
 
 `<-- Anterior <gerente.rst>`_ <- - -> `Próximo --> <menus_auxiliares.rst>`_