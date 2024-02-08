A demonstration of Docker to implement a simple 3 tier architecture

* frontend will be able to access the mid-tier
* mid-tier will be able to access the db

In order to run this in docker, simply type ```docker-compose up``` at the command prompt. Docker will then create the [MongoDB](https://www.mongodb.com/) from the stock [mongo](https://hub.docker.com/_/mongo) image. The api uses [nodejs](https://nodejs.org/) with [express](http://expressjs.com/) and is built from a [node:alpine](https://hub.docker.com/_/node) image. The front end uses [ReactJS](https://reactjs.org/) and built from a [node:alpine](https://hub.docker.com/_/node) image.

first approach        

docker run -d -e MONGODB_INITDB_ROOT_USERNAME=gopal -e MONGODB_INITDB_ROOT_PASSWORD=gopal --name mongo --network frontend  mongo

docker run -d --name backend-con -p 3001:3001 --network=frontend  backend

docker run -d --name frontend -p 3000:3000 --network=frontend  frontend

second approach
docker run -d -e MONGODB_INITDB_ROOT_USERNAME=gopal -e MONGODB_INITDB_ROOT_PASSWORD=gopal --name mongo  mongo

docker run -d --name backend-con -p 3001:3001 --link mongo:mongo  backend

docker run -d --name frontend -p 3000:3000  frontend

#### http://localhost:3001/api
#### http://localhost:3001/api/todos
