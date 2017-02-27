# docker-compose
Docker Setup for a complete PHP7 Dev Environment (Includes XDEBUG integration)


## Sugested folder structure: 

- ~/your_workspace/
  - **docker-compose**/
    - docker-compose.yml
    - docker/php/
      - Dockerfile
      - php.ini
      - xdebug.ini
  - applications/
  - nginx/
    - conf.d/
  
## RUN

```
mkdir -p ~/workspace/applications
mkdir -p ~/workspace/nginx/conf.d
cd ~/workspace && git clone https://github.com/mauriciovander/docker-environment.git
cp -r docker-environment/example/applications/info applications
cp docker-environment/example/nginx/conf.d/info.conf nginx/conf.d
sed -i -- "s/{{HOST_IP}}/`ipconfig getifaddr en0`/g" docker-environment/docker/php/*.ini
cd docker-environment && docker-compose up -d

docker ps
```

In PHP Storm, point your debug server to the IP address obtained by:
```
docker inspect -f"{{.NetworkSettings.IPAddress}}" dockerenvironment_php_server_1
```
- HOST {{IP_ADDRESS}}
- PORT: 9000
- IDE KEY: PHPSTORM


### Happy coding!

Add your projects to the `applications` folder, create nginx .conf files and point your local domain names to `127.0.0.1` in your `/etc/hosts` file

(if 127.0.0.1 doesn't work, use the IP of your Docker default machine)


### Note: 
If you change your host to a different network, you'll need to edit the files in 
docker-environment/docker/php/*.ini to the new IP address of your host.
After doing that, create again the php_server image

get the list of active containers: 
```
docker ps
```
```
CONTAINER ID        IMAGE                         ...   NAMES
c10942823941        dockerenvironment_php_server  ...   dockerenvironment_php_server_1
```
```
docker stop dockerenvironment_php_server_1
docker rm dockerenvironment_php_server_1
docker image rm dockerenvironment_php_server
```
Create the container
```
docker-compose up -d
```
