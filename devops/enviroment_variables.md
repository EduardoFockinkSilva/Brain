Variáveis de ambiente são um conjunto de valores nomeados armazenados no sistema operacional, que são usados por processos em execução. Essas variáveis podem ser usadas para controlar o comportamento de vários programas. Por exemplo, a variável de ambiente PATH especifica diretórios nos quais o sistema deve procurar comandos.

As variáveis de ambiente são essenciais no Linux e em outros sistemas operacionais baseados em Unix, pois permitem a configuração de detalhes do ambiente de execução do sistema e de aplicativos.

Visualizando Variáveis de Ambiente:

Comando printenv: Para visualizar todas as variáveis de ambiente, você pode usar o comando printenv sem argumentos:

bash
printenv

Se você quiser visualizar uma variável de ambiente específica, por exemplo, HOME, use:

bash
printenv HOME

Comando echo: Variáveis de ambiente podem ser acessadas colocando $ antes do nome da variável. Por exemplo:

bash
echo $HOME

Configurando Variáveis de Ambiente:

Temporariamente (durante a sessão atual): Você pode definir ou modificar uma variável de ambiente usando o comando export:

bash
export VAR_NAME=value

Por exemplo, para definir a variável MY_VAR com o valor HelloWorld, você usaria:

bash
export MY_VAR=HelloWorld

Permanentemente:

Arquivo ~/.bashrc: Para adicionar ou modificar variáveis de ambiente permanentemente para um usuário específico, você pode adicionar o comando export ao arquivo ~/.bashrc do usuário.

Arquivo /etc/environment: Se você quiser definir variáveis de ambiente globalmente, para todos os usuários, pode adicionar as definições ao arquivo /etc/environment. Neste arquivo, a sintaxe é ligeiramente diferente, pois o comando export não é usado. Por exemplo:

makefile
VAR_NAME=value

Após modificar qualquer um desses arquivos, você deve executar o comando source para aplicar as mudanças:

bash
source ~/.bashrc

ou, para /etc/environment:

bash
source /etc/environment

É importante lembrar que variáveis de ambiente são sensíveis ao caso (case-sensitive) no Linux, ou seja, VarName e varname seriam consideradas variáveis diferentes. Além disso, o processo de definição e visualização pode variar ligeiramente dependendo do shell que você estiver usando (bash, zsh, csh, etc.).

Pricnipais variaveis de ambiente

echo $?