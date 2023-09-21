# Docker: Containerization Simplified

## Overview

Docker is a platform for developing, shipping, and running applications in lightweight, portable containers. These containers encapsulate an application and its dependencies, allowing it to run consistently across various computing environments. Docker relies on OS-level virtualization, which makes it less resource-intensive than traditional virtual machines.

[Wikipedia](https://en.wikipedia.org/wiki/Docker_(software))

[Official Website](https://www.docker.com/)

[Documentation](https://docs.docker.com/)

## Installation and Initial Configuration

### Installing Docker Engine

Docker Engine is available for multiple operating systems including Linux, macOS, and Windows. Below is an example installation on a Ubuntu-based system.

```
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
```

### Post-Installation Steps

After installation, you may want to add your user to the `docker` group to run Docker commands without `sudo`.

```
sudo usermod -aG docker $USER
```

## Docker Architecture and Components

### Docker Daemon

The background service running on the host that manages building, running and distributing Docker containers.

### Docker CLI

Command-line interface tool that allows the user to interact with the Docker daemon.

### Docker Hub

A registry service for sharing container images. You can think of it as GitHub but for Docker images.

## Container Lifecycle Management

### Starting a New Container

To start a new container from an image:

```
docker run IMAGE_NAME
```

### Managing Containers

List, stop, start, and remove containers:

```
docker ps
docker stop CONTAINER_ID
docker start CONTAINER_ID
docker rm CONTAINER_ID
```

## Images and Registries

### Pulling Images

Download an image from a registry (like Docker Hub).

```
docker pull IMAGE_NAME:TAG
```

### Building Images

Build an image from a Dockerfile.

```
docker build -t IMAGE_NAME:TAG PATH_TO_DOCKERFILE
```

## Docker Compose

Docker Compose is a tool to define and manage multi-container Docker applications. Configuration is usually stored in a `docker-compose.yml` file.

### Basic Commands

```
docker-compose up
docker-compose down
```

## Networking

Docker has various networking options to link containers, expose ports, and even create custom bridges.

### Basic Networking Commands

```
docker network ls
docker network create NETWORK_NAME
docker network rm NETWORK_NAME
```

## Storage and Volumes

Docker allows mounting volumes for persistent storage and data sharing between containers.

```
docker volume create VOLUME_NAME
docker volume ls
docker volume rm VOLUME_NAME
```

## Best Practices

- Use `.dockerignore` files to exclude files that are not necessary for building a Docker image.
- Always specify a tag when pulling images. E.g., `docker pull nginx:1.19` instead of `docker pull nginx`.
- Use multi-stage builds for minimizing image size.
- Use official base images whenever possible.
- Regularly update images for security patches.









# Dicas de Docker para Linux



## Atividade 1 ---- INSTALAÇÃO 


Opções:  

> --> Mint 20

	$ sudo apt install docker
	$ sudo apt install docker.io 


> --> Linux Mint 19:  

	https://gist.github.com/sirkkalap/e87cd580a47b180a7d32  


> --> Linux Mint 18:  

	https://gist.github.com/andrewelkins/1adc587feb610f586f8f40b50b7efc3a#file-install-docker-on-linux-mint-18-sh  




> --> Shell - arquivo baixado na pasta  

	$ sudo sh Install-Docker-on-Linux-Mint.sh  


> --> Oficial docker   

	https://docs.docker.com/install/linux/docker-ce/ubuntu/  


> --> Ubuntu de 64 Bits, versão 13.04:  

	https://www.digitalocean.com/community/tutorials/como-instalar-e-utilizar-o-docker-primeiros-passos-pt  


> --> Direto do shell  

	$ wget -qO- https://get.docker.com  




### Adicionar usuário ao grupo docker para evitar sudo

> sudo usermod -aG docker ${USER}


		$ sudo usermod -a -G docker <<seu-user-name>>




## Atividade 1.1 ---- GERENCIAMENTO 

#### Status
			$ top  
			$ ps -fax  
			$ ps -ef | grep docker  
			$ pgrep docker  
			$ sudo systemctl status docker   -->		q (quit) para sair  


#### Start 

			$ sudo systemctl start docker


#### Stop 

			$ sudo systemctl stop docker  
			ou  
			$ sudo /etc/init.d/docker stop  


#### Info

			$ sudo docker info



## Atividade 1.2 ---- TESTE

			$ sudo docker run hello-world





## Atividade 2 ---- GERENCIAR IMAGENS PRONTAS  



###		Exibir imagens locais   

			$ sudo docker images  


###		Procurar por imagens prontas   

			sudo docker search `nome_da_imagem`

>			Exemplo:  
>			$ sudo docker search ubuntu  
>			$ sudo docker search mysql  
>			$ sudo docker search mongo  


>			Shared images:  
>			https://hub.docker.com/  
>			https://hub.docker.com/search/?type=image  






###  Baixar/instalar imagens prontas

		 	sudo docker pull `nome_da_imagem`
			
>			$ sudo docker pull ubuntu



###  Inspecionar imagens

		 	sudo docker image inspect `IMAGE_ID`
			
>			$ sudo docker image inspect ubuntu 



###		Excluir imagem

			$ docker rmi `IMAGE_ID` 






## Atividade 3 ---- GERENCIAR CONTAINERS
 


###		Exibir containers ativos

			$ sudo docker ps       

###		Exibir todos os containers 

			$ sudo docker ps -a    


###		Criar um container  


			$ sudo docker run ubuntu  
			$ sudo docker ps -a  


###		Criar um container com nome

			$ sudo docker run --name ubuntupadoin ubuntu    
			$ sudo docker ps -a  





###		Criar e Executar um container 


			$ sudo docker run -i -t ubuntu /bin/bash  
			ou  
			$ sudo docker run -it ubuntu /bin/bash  
			ou  
			$ sudo docker run -it --name ubuntupadoin2 ubuntu   /bin/bash  

>							opções:  
>								-i permite interagir com o container    
>								-t associa o seu terminal ao terminal do container  
>								-it é apenas uma forma reduzida de escrever -i -t  
>								--name algum-nome permite atribuir um nome ao container em execução  
>								-p 8080:80 mapeia a porta 80 do container para a porta 8080 do host  
>								-d executa o container em background  
>								-v /pasta/host:/pasta/container cria um volume '/pasta/container' dentro do container com o conteúdo da pasta '/pasta/host' do host  

>								--detach , -d		Detached mode: run command in the background  
>								--detach-keys		Override the key sequence for detaching a container  
>								--env , -e			API 1.25+ Set environment variables  
>								--interactive , -i	Keep STDIN open even if not attached  
>								--privileged		Give extended privileges to the command  
>								--tty , -t			Allocate a pseudo-TTY  
>								--user , -u			Username or UID (format: <name|uid>[:<group|gid>])  




###		Sair de um container em execução

			$ exit




###		Excluir  containers

			$ sudo docker rm `CONTAINER ID`  

			$ sudo docker rm --force `CONTAINER ID`  
  






## Atividade 4 ---- TRABALHAR COM CONTAINERS - attach


###		Criar um container ativo em backgroud

			$ sudo docker run -it -d --name padoin5 ubuntu   /bin/bash  
	
			$ sudo docker ps -a  



###		Entrar em um container ativo e em backgroud  

			$ sudo docker attach CONTAINER_ID  


### 		Sair de um container em execução  

			$ exit  






## Atividade 4.1 ---- TRABALHAR COM CONTAINERS - exec


###		Ativar um container 

			$ sudo docker ps -a  

			$ sudo docker start padoin5  

			$ sudo docker ps -a  



### 	Executar um comando em um container ativo sem entrar no container

			$ sudo docker exec -i -t padoin5 ls 




###		Parar um container ativo

			$ sudo docker stop padoin5

			$ sudo docker ps -a 







## Atividade 5 ---- TRABALHAR COM CONTAINERS - 



  $  sudo docker run -it --name padoin44 ubuntu   /bin/bash  
  	 exit <----- dentro do container  

  $  sudo docker ps -a  
  $  sudo docker start padoin44  
  $  sudo docker ps -a  
  $  sudo docker attach padoin44   
  	 mkdir segunda		             <----- dentro do container  
  	 mkdir terca			             <----- dentro do container  
  	 exit                          <----- dentro do container  
 
  $  sudo docker start padoin44  
  $  sudo docker attach padoin44    
			ls 		             <----- dentro do container  - as pastas estão no container

####		Sair de um container e deixá-lo ativo
	$   CTRL + P CTRL + Q 

  $  sudo docker ps -a   
  $  sudo docker stop padoin44  








## Atividade 6 ---- CRIAR IMAGENS 

###		Criar um arquivo Dockerfile

>			dica: 	somente um Dockerfile por diretorio  

conteúdo do arquivo:

>				FROM    # deve ser a primeira instrução - de qual imagem base vou criar a minha
>				RUN  		# comando que vai ser rodado na instalação
>				ENV     #
>				CMD     # deve ser a última instrução - qual comando vai ser executado qdo o container for levantado


Exemplo Dockerfile com serviço de rede:

$ nano Dockerfile  
>					FROM ubuntu
>					MAINTAINER padoin
>					RUN apt-get -y update
>					RUN apt-get -y install net-tools
>					RUN apt-get -y install iputils-ping



###		Criar a imagem com o arquivo Dockerfile 
	
>			sudo docker build -t <nome_da_minha_imagem:versao> <local a ser criado ponto "." é no local atual >

			$ sudo docker build -t ubuntu:2903 -f Dockerfile .



###		Exibir imagens locais  

			$ sudo docker images  




###		Executar um container a partir de uma imagem criada  

			$ sudo docker run -it ubuntu:2903 /bin/bash  



###		Sair de um container ativo  

			$ exit  





## Atividade 7 ----  UTILIZAR UM CONTAINER CRIADO




###		Executar um container com a imagem criada

			$ sudo docker run -it ubuntu:2903 /bin/bash


			$ ifconfig   <----------------- no container 


####		Sair de um container e deixá-lo ativo

			$ CTRL + P CTRL + Q   

			$ ping 172.17.0.3    <----------------- fora do container com o IP do container   

			$ sudo docker ps   

			$ sudo docker stop CONTAINER_ID  





## Atividade 8 ---- USAR CONTAINER CRIADO
 

###		Executar um container com a imagem criada

			$ sudo docker run -it ubuntu:2903 /bin/bash



###		Sair do container e deixá-lo ativo
 
			$ CTRL + P CTRL + Q    



### 	Executar um comando em um container ativo


			$ sudo docker ps -a  

			$ sudo docker exec -i -t CONTAINER_ID ls  
		 	$ sudo docker exec CONTAINER_ID mkdir /sd2023/  
			$ sudo docker exec -i -t CONTAINER_ID ls  

			$ sudo docker exec -i -t CONTAINER_ID ifconfig  	
			$ ping 172.17.0.3   
			$ CTRL + C para cancelar o ping   




###	Entrar em um container ativo e em backgroud

			$ sudo docker attach CONTAINER_ID  

			ls <----- para verificar se foi criado  


###		Sair de um container ativo

			$ exit




## Atividade 9 ---- CONTAINERS com usuários



#### 1 criar uma imagem com usuário

>	criar uma pasta com seu nome

	$ mkdir padoinativ9 

> 	entrar na pasta criada

	$ cd padoinativ9

>	criar um arquivo Dockefile com o seguinte conteudo

$ nano Dockerfile2  

				FROM ubuntu   
				MAINTAINER padoin  
				RUN mkdir -p /test  
				RUN useradd appuser   
				RUN usermod -a -G sudo appuser  
				USER appuser  


> 	criar uma imagem  

			$ sudo docker build -t ubuntu:5 -f Dockerfile2 .


#### 2 criar um container com a imagem e executar com o usuário

			$ sudo docker run -i -t -u appuser  ubuntu:5 /bin/bash





## Atividade 10 ---- UM CONTAINER com pasta compartilhada (volumes)


 
> 	criar uma pasta no seu home  

	$ cd ~  
	$ mkdir meudir  


> 	criar um container conectando a pasta no seu home (meudir) com a pasta do container (test)

>			dica:  
>			- diretorio_do_home:diretorio_do_container  
>			- a pasta testSD será criada dentro do container  

	$ sudo docker run -v /home/padoin/meudir:/testSD -i -t ubuntu /bin/bash

> para testar crie e edite arquivos no 
>	diretorio_do_home chamado `meudir` e no diretorio_do_container chamado de `testSD`

#### no container
			$ cd testSD
			$ echo "sistemas distribuídos" > a.txt
			$ ls
			$ CTRL + P CTRL + Q 		

#### no home
			$ cd meudir
			$ ls
			$ cat a.txt
			$ echo "usando docker com volumes" > b.txt

			$ sudo docker ps -a 
 			$ sudo docker attach `NOME DO CONTAINER`

#### no container
			$ ls
			$ cat b.txt	
			$ exit





## Atividade 10.1 ---- DOIS CONTAINERS com pasta compartilhada (volumes)


> 	criar uma pasta no seu home  

	$ cd ~  
	$ mkdir pastacompartilhada

> 	criar dois containers conectando com a `pasta compartilhada` 
>   container 1 com nome padoin55  
>   container 2 com nome padoin66

			$ sudo docker run -v /home/padoin/pastacompartilhada:/pastashared -i -t  -d --name padoin55 ubuntu /bin/bash

			$ sudo docker ps

			$ sudo docker run -v /home/padoin/pastacompartilhada:/pastashared -i -t  -d --name padoin66 ubuntu /bin/bash

			$ sudo docker ps


>   no shell 1 trabalhar no container padoin55  
			$ sudo docker exec -i -t padoin55 ls  

			$ sudo docker attach padoin55 
				$ cd pastashared
				$ echo "testando 1" > a.txt
				$ ls  
				$ cat  a.txt
				$ CTRL + P CTRL + Q 


>   no shell 2 trabalhar no container padoin66  
			$ sudo docker exec -i -t padoin66 ls  

			$ sudo docker attach padoin66  
				$ cd pastashared
				$ echo "testando 2" >> a.txt
				$ ls  
				$ cat  a.txt
				$ CTRL + P CTRL + Q 


>   fora dos containers  
			$ cd pastacompartilhada
			$ cat a.txt

>   parar os containers  
			$ sudo docker ps 
			$ sudo docker stop padoin55
			$ sudo docker stop padoin66
			$ sudo docker ps 






## Atividade 11 ---- FUNÇÕES AVANÇADAS - commit


###		Salvando (committing) um container

>		criar uma nova imagem a partir do container   

			$ sudo docker ps -a

			$ sudo docker commit padoin55  padoin77

			$ sudo docker images






## Atividade 12 ---- FUNÇÕES AVANÇADAS - push

>		enviar uma imagem para o hub

			$ docker push 





 


### verificar local das imagens e containers


	$ sudo ls  /var/lib/docker/containers -l  
 
	$ sudo ls  /var/lib/docker/image -l  







### Ref

https://docs.docker.com/

https://docs.docker.com/get-started/  

https://docs.docker.com/engine/reference/commandline/image_ls/

https://aws.amazon.com/pt/getting-started/deep-dive-containers/?e=gs2020&p=gsrc