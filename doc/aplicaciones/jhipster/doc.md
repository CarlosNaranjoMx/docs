| |version|
|---|---|
|nvm|0.31.3|
|node|v16.16.0|
|npm|8.11.0|
|java|11.0.15|
|maven|3.8.6|
|Client: Docker Engine|20.10.22|
|Docker Compose|v2.14.1|

# Steps

1. Install nvm
~~~
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.3/install.sh | bash
~~~

2. Install version 16.16.0 node, compatible with jhipster
~~~
nvm install 16.16.0
~~~

3. Install `jhipster`
~~~
npm install -g jhipster-generator
~~~

4. Install java jdk
~~~
sudo dpkg -i  jdk-17_linux-x64_bin.deb
~~~

5. Agregar `JAVA_HOME`
~~~
export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
~~~

6. Descargar e instalar maven, añadirlo al path
~~~
export PATH=/opt/apache-maven-3.8.6/bin:$PATH
~~~

7. Install docker

-El client de Docker es un programa de computadora que se puede usar para hacer
configuraciones de Docker.

-El client de Docker se puede usar para hacer configuraciones de Docker para
todos los usuarios del sistema.

-Docker Compose es una forma de crear configuraciones de Deploy para servicios
de la application y los servicios de la application en una application de
contenedores.

~~~
sudo apt -y install apt-transport-https ca-certificates curl software-properties-common
sudo apt -y remove docker docker-engine docker.io containerd runc
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu jammy stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
~~~
- instalar
~~~
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin
~~~
- agregar usuarios a el grupo
~~~
sudo usermod -aG docker $USER
newgrp docker
~~~

8. Instalar docker compose
~~~
curl -s https://api.github.com/repos/docker/compose/releases/latest | grep browser_download_url  | grep docker-compose-linux-x86_64 | cut -d '"' -f 4 | wget -qi -
chmod +x docker-compose-linux-x86_64
sudo mv docker-compose-linux-x86_64 /usr/local/bin/docker-compose
~~~

`dcoker-compose.yml`
~~~
version: '3'  
services:
  web:
    image: nginx:latest
    ports:
     - "8080:80"
    links:
     - php
  php:
    image: php:7-fpm
~~~
`docker-compose up -d`
`docker-compose ps`
`docker-compose stop`
`docker-compose rm -f`