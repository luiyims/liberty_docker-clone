# liberty_docker

Para la configuracion hacer lo siguiente

1. en el archivo ./apache/docker-compose.yaml y el archivo ./php/docker-compose.yaml
   - ir a donde dice volume
     - cambiar ../../flowbusiness_co por la carpeta donde se encuentre flowbusiness
       - ../../flowbusiness_co:/usr/local/apache2/htdocs/flowbusiness_co
     - cambiar ../../cwbusiness.com/core por la carpeta donde se encuentre el core de cwcbusiness
       - ../../cwbusiness.com/core:/usr/local/apache2/htdocs/cwbusiness

Ejecutar los siguientes comandos:

1. para crear la net:
   ```shell script
   docker network create cw_net
   ```
2. para iniciar el mysql:
   ```shell script
   docker-compose -f ./mysql/docker-compose.yaml up -d
   ```
3. para iniciar el php:
   ```shell script
   docker-compose -f ./php/docker-compose.yaml up -d
   ```
4. para iniciar el apache:
   ```shell script
   docker-compose -f ./apache/docker-compose.yaml up -d
   ```

Mysql dump.zip LFS

1. install LFS for git
   ```shell script
   brew install git-lfs
   ```
2. enable LFS
   ```shell script
   git lfs install
   ```
3. enable LFS system
   ```shell script
   git lfs install --system
   ```
