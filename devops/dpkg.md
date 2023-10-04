dpkg
1. Visão Geral
dpkg é o sistema de gerenciamento de pacotes de baixo nível do Debian. Ele não lida diretamente com repositórios ou fontes, como o APT. Em vez disso, o dpkg instala, remove e fornece informações sobre pacotes .deb, que são os arquivos de pacote binário do Debian.

2. Funcionalidades Básicas
Instalação: O dpkg pode instalar pacotes a partir de arquivos .deb.

bash
Copy code
dpkg -i nome_do_pacote.deb
Remoção: Ele também pode remover pacotes instalados.

bash
Copy code
dpkg -r nome_do_pacote
Consultas: O dpkg pode ser usado para consultar o banco de dados local de pacotes instalados.

bash
Copy code
dpkg -l
bash
Copy code
dpkg -s nome_do_pacote
Configuração: Se, por alguma razão, um pacote não estiver configurado (por exemplo, após uma instalação incompleta), pode ser configurado usando:

bash
Copy code
dpkg --configure nome_do_pacote
Extração: Os pacotes .deb podem ser extraídos para inspeção.

bash
Copy code
dpkg -x nome_do_pacote.deb /caminho/para/diretorio
3. Dependências
O dpkg não resolve dependências como o APT. Se tentar instalar um pacote que depende de outros pacotes que não estão instalados, o dpkg irá reclamar. O APT é a ferramenta que, na verdade, lida com a resolução de dependências, fazendo uso do dpkg para as operações de instalação/remoção.

4. Arquivos de Configuração
Ao remover pacotes usando dpkg, os arquivos de configuração não são removidos por padrão. Usar a opção --purge ao remover irá eliminar estes arquivos de configuração.

5. Banco de Dados
O dpkg mantém um banco de dados de todos os pacotes instalados em /var/lib/dpkg. Este banco de dados é vital para o funcionamento correto do gerenciamento de pacotes no sistema.

6. dpkg e APT
Enquanto o dpkg lida diretamente com os pacotes .deb, o APT lida com repositórios e resolve dependências. O APT faz uso do dpkg para instalação, atualização e remoção de pacotes.

7. Utilização Profissional
Em ambientes profissionais e de produção, é recomendado usar o APT para instalar pacotes, pois ele gerencia automaticamente as dependências. O dpkg é geralmente usado em cenários mais específicos, como durante o desenvolvimento de pacotes ou quando se deseja instalar um pacote específico que não está disponível nos repositórios padrão.