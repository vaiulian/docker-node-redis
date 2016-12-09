## REDIS SERVER

> `cd redis`

- run docker redis container from redis image

> `docker run -d --name redis -p 6379:6379 redis`

**OR**


- create docker image for redis (from /redis folder)
> `docker build -t iuva/redis .`

- run docker container from that iuva/redis new image
> `docker run -d --name redis -p 6379:6379 iuva/redis`



## NODE SERVER

> `cd node`

- create docker image for node (from /node folder)

> ` docker build -t iuva/node .`

- run docker container from that iuva/node new image

> `docker run -d --name node -p 8080:8080 --link redis:redis iuva/node`

### **OR [optional] please run from docker-compose up, instead !!!!!!!**



- create docker image for node (from /node folder)
> `docker build -t iuva/node .`

- run docker container with -v volume mounted i.e. local folder of my app, in order to update files onsave from host to container
> `docker run -d --name node -p 8080:8080 -v C:/Users/iuva/work/docker/node-redis/node:/src/ --link redis:redis iuva/node`

- [optional] exec node install if node_modules was overridden by -v option
> `docker exec -d --name node npm install`

- [optional] exec nodemon -L i.e. legacy mode if nodemon doesn't restart server when files are updated on host machine
> `docker exec -d --name node nodemon -L index.js`



## DOCKER COMPOSE

- creates images and start containers
- -d (in background mode) --build (force rebuild of images)
> `docker-compose up -d --build`

- stop all containers
> `docker-compose stop`

- remove all containers
> `docker-compose rm`