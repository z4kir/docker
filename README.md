# Docker
This is Docker learning repo

# Table Of Content
*[Docker Version](#check-docker-version)

*[Docker Image](#image)

*[Docker Container](#docker-container)

*[Nginx In Docker](#nginx-in-docker)

*[Mysql In Docker](#mysql-in-docker)

## Check Docker Version 
 `docker -v`
 
#### create docker volume
`docker volume`

#### login to docker hub
`docker login`

#### logout to docker hub
`docker logout`
## Image

### Pull Docker Image
`docker pull [imageName]`

### Push Docker Image
`docker push [imageName]`

### Build Image
`docker build -t [give imageName] [directory (. for current directory)]`

### Build by given Image name
`docker build -f [given image name] -t [give imageName] [directory (. for current directory)]`

### commit Docker 
`docker commit`

### copy image
`docker copy [imageName]`



### Image list
`docker images`

### Image search
`docker search [searchQuery]`

### Run Image to make Docker Container
`docker run [imageName/imageId]`
`docker run --name [Give the name to the container] -d [imageName/imageId]     (-d -> detached) | use -it before -d to run in background (-it -> interactive mode)`

## Docker Container

### List of Docker Containers
`docker ps (currently running container)`
`docker ps -a (all the container)`

### Inspect Container (Gets all information about container)
`docker inspect [containerId]`

### container Logs
`docker logs [containerName/containerId]`

### Start command of container
`docker container start [containerName/containerId]`

### Execute command of running container
`docker exec -it [containerId] [command/code to execute]`

### stop command of running container
`docker stop [imageName/imageId]`

### remove command of  container
`docker rm [imageName/imageId]`

### restart command for container
`docker restart [imageName/imageId]`

### check port mapping
`docker port [containerName/containerId]`

### See File of container inside docker
`docker exec -it [containerId/containerName] bash`


## Nginx in Docker

(-- containerName is nginx-base)

### copy default.conf to givenFolder/file
`docker cp nginx-base:/etc/nginx/conf.d/default.conf default.conf      (here default.conf is given file name)`

#### After do configuration re-past default.conf to nginx server file 
`docker cp default.conf nginx-base:/etc/nginx/conf.d/default.conf`

### nginx validation of config file
`docker exec [containerName/containerId] nginx -t`

### nginx reload config file
`docker exec [containerName/containerId] nginx -s reload`



## MySql in Docker

### Run Mysql on different port (3306->3307)
 `docker run -d --name [given container name] -e MYSQL_ROOT_PASSWORD=strong_password -p 3307:3306 mysql`

### full mysql run command
```docker run --name mysql8 -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=testdb -e MYSQL_USER=admin -e MYSQL_PASSWORD=root -d mysql:8.0.20```

### Mysql server run
`docker exec -it mysqlDb  bash`

### Mysql User Creation with all the access
creating user
`create user 'user'@'%' identified by 'pass';`
Giving roles and access to user
`grant all privileges on *.* to 'user'@'%' with grant option`;
`flush privileges`;
