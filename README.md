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
mkdir -p ~/workspace/applications
mkdir -p ~/workspace/nginx/conf.d
cd ~/workspace 
git clone https://github.com/mauriciovander/docker-compose.git
cd ~/workspace docker-compose 
docker-compose up -d

### Happy coding!
