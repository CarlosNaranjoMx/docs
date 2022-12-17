| |version|
|---|---|
|nvm|0.31.3|
|node|v16.16.0|
|npm|8.11.0|
|java|11.0.15|
|maven|3.8.6|

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