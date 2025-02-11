## Configuração do Docker

Antes de realizar a instalação do Portainer, é necessário confirmar que o ambiente Docker esteja previamente operando.

Link para obtenção dos pacotes oficiais + documentação oficial
 https://docs.docker.com/engine/install/ubuntu/

 1) Instalação dos pacotes necessários:

    
    sudo apt install -y ca-certificates curl gnupg

3) Adição do repositório oficial do Docker


   sudo install -m 0755 -d /etc/apt/keyrings
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo tee /etc/apt/keyrings/docker.asc > /dev/null


   sudo chmod a+r /etc/apt/keyrings/docker.asc

4) Comando para instalar o Docker

sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin


5) Para confirmar que a instalação foi bem sucedidada, pode-se usar este comando:

docker --version


6) Para ativar o Docker e definir o início como automático, deve-se utilizar o seguinte comando:


sudo systemctl enable docker

sudo systemctl start docker


## Configuração do Portainer
O Portainer pode ser instalado através do docker-compose.yml (arquivo presente neste repositório) ou através do docker run abaixo:

docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

Após utilizar o docker run, o serviço ficará acessível na porta configurada no arquivo yml, de acordo com o docker run irá iniciar no https://localhost:9443
