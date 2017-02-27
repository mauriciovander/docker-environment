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
docker inspect -f"{{.NetworkSettings.IPAddress}}" dockerenvironment_php_server_1
```

### Happy coding!
