== Instalação do Docker ==

1) Para instalar o Docker, é necessário instalar os pacotes que comunicam diretamente com o repositório HTTPS:
-> sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common

2) Adicione a chave GPG oficial do Docker, para validar os pacotes:
-> curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

3) Adicione o repositório do Docker:
-> echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

4) Verifique se a instalação ocorreu corretamente:
-> sudo Docker --version

== Instalação e utilização do Docker Compose ==
O Docker Compose é uma ferramenta que permite a integração de imagens que contém mais de um container. Através de um arquivo YAML, é possível definir parâmetros de importação como volumes, containers, networks e mais valores personalizáveis.

1) Comando para baixar o Docker Compose
-> sudo curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep -Po '"tag_name": "\K.*\d')" /usr/local/bin/docker-compose

2) Dê permissão para o binário do Docker Compose:
-> sudo chmod +x /usr/local/bin/docker-compose

3) Verifique se a instalação foi bem-sucedida:
-> docker-compose --version

== Instalação do Portainer via Docker Compose ==
O Portainer é uma ferramenta de gestão que oferece ao usuário uma interface referente as dependências Docker, através dele é possível verificar e interagir com os aplicativos, imagens, volumes e networks. É uma ferramenta de grande valia para usuários que não tem tanta intimidade com gerenciamento através de linhas de comando do Docker.

1) Criar um repositório referente a instalação do Portainer
-> mkdir Portainer

2) Criar o arquivo com as instruções do Portainer:
-> Para criar o arquivo use o comando (nano docker-compose.yml)
-> Preencha os seguintes valores:
   version: '3.3' 

   services:
	portainer:
           image: portainer/portainer-ce:latest
	   container_name: portainer
   	   restart: Always
  	   ports:
		-"9000:9000"
	volumes:
	  - /var/run/docker.sock:/var/run/docker.sock
	  - portainer_data:/data

  volumes:
    portainer_data:

3) Inicie o Portainer com o Docker Compose
-> docker-compose up -d

4) Ao efetuar os procedimentos anteriores, a instalação será finalizada e a interface web do Portainer será acessível pela porta definida no docker-compose.yml, neste caso foi a porta 9000.
-> Acesse http://seu-ip:9000

5) Para gerenciar os containers rodando, basta rodar o comando:
-> docker ps


