/ (Raiz)
Descrição: Este é o diretório raiz. Todos os outros diretórios, arquivos, montagens, dispositivos, etc., estão contidos nele.
/bin (Binários)
Descrição: Contém comandos/binários essenciais para o funcionamento do sistema, especialmente os necessários para a inicialização e reparo do sistema.
/sbin (Binários de Sistema)
Descrição: Similar ao /bin, mas contém binários que são geralmente executados pelo superusuário (root) para tarefas de administração do sistema.
/boot
Descrição: Contém arquivos relacionados ao processo de inicialização, como o kernel (vmlinuz), a imagem de disco inicial (initrd ou initramfs), e o bootloader (por exemplo, grub).
/dev (Dispositivos)
Descrição: Contém arquivos de dispositivo que representam dispositivos físicos e virtuais no sistema, como discos rígidos (/dev/sda), terminais (/dev/tty1), etc.
/etc (Etcetera)
Descrição: Mantém arquivos de configuração do sistema e scripts de inicialização de serviços. Qualquer software ou pacote instalado no sistema que precisa ser globalmente configurado terá arquivos de configuração aqui.
/home
Descrição: Diretório onde ficam os diretórios pessoais dos usuários normais. Por exemplo, /home/eduardo seria o diretório home do usuário eduardo.
/lib e /lib64
Descrição: Estes diretórios contêm bibliotecas compartilhadas necessárias para a inicialização do sistema e para a execução de comandos/binários em /bin e /sbin.
/opt (Opcional)
Descrição: Destinado a software e pacotes opcionais de terceiros. Softwares que não fazem parte da distribuição padrão geralmente são colocados aqui.
/proc (Processo)
Descrição: Sistema de arquivos virtual que fornece informações sobre processos e outras informações do sistema. Não contém arquivos reais, mas endpoints que oferecem uma visão do kernel do sistema.
/root
Descrição: Diretório pessoal do superusuário (root).
/run
Descrição: Sistema de arquivos temporário que armazena informações voláteis sobre o sistema em execução e é montado como tmpfs.
/tmp (Temporário)
Descrição: Diretório que contém arquivos temporários criados por sistemas e programas. Geralmente é limpo a cada reinicialização.
/usr (Unix System Resources)
Descrição: Contém binários, bibliotecas, documentação e códigos-fonte para programas de segundo nível (i.e., programas não essenciais para a inicialização).
/var (Variável)
Descrição: Diretório que armazena dados variáveis e em constante mudança, como logs, bancos de dados, websites e caches. Os subdiretórios mais comuns são:

/var/log: Contém arquivos de log para a maioria dos sistemas e serviços.

/var/spool: Usado para armazenar tarefas esperando para ser processadas, como e-mails e trabalhos de impressão.

/var/tmp: Similar a /tmp, mas os arquivos aqui não são necessariamente excluídos entre as reinicializações.

/var/lib: Armazena dados dinâmicos e informações de estado para programas, como bancos de dados de atualizações do sistema.

/var/www: Comumente usado para armazenar documentos do servidor web, como sites hospedados em um servidor Apache.

/mnt (Mount)
Descrição: Tradicionalmente usado para montar sistemas de arquivos temporariamente, como unidades USB ou discos externos.
/media
Descrição: Semelhante ao /mnt, mas geralmente reservado para montagens automáticas de dispositivos removíveis, como CDs, unidades USB e outros dispositivos de armazenamento.
/sys (Sistema)
Descrição: Como /proc, é um sistema de arquivos virtual que fornece uma interface para informações do kernel sobre dispositivos, drivers e algumas outras características do kernel.
/srv (Service)
Descrição: Diretório para dados específicos do serviço do site. A ideia é que, ao hospedar, por exemplo, um servidor FTP e um servidor web, os dados para ambos podem ser colocados aqui em /srv/ftp e /srv/www, respectivamente.