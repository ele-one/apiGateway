# apiGateway
- Load balacing
- Forward Proxy
- Caching (plan to)


### FLow?

- client/browser hits the nginx first running at port 7777.
- nginx root '/' directs the client to the apiGateway service
- apiGateway service compose the UI by aggregating the UI of all the services


### How to run the code?
- run nginx is running and
- run docker-compose up to build and start containers.


Place nginx to the right path (more info in the nginx_brown.conf file) and start nginx,
``` nginx ```

Helpful Commands

```
nginx -s reload
nginx -s stop
nginx

```


NOTE: When change the nginx.conf file, restart the services running in docker,

```
docker-compose restart
docker-compose up
```

Helpful Commands

```
After starting the docker-compose, you'll see the process running and listening to the respective ports.

netstat -an | grep 'LISTEN'


docker-compose start
docker-compose restart
docker-compose stop


Use docker-compose stop to stop the processess and verify
netstat -an | grep LISTEN

```


If you made any code changes in any service such as in App.jsx of crud service, you need to build the docker image again.

To build that one service and not all, do

``` docker-compose build crud ```

To build all services do:

``` docker-compose build ```



Note: docker-compose.yml file used by docker-compose command to tell it what to do.

Dockerfiles present in each service is for building the image used by ``` docker build -t <service name> . ```
They can be used to build individually and manually build each service.

We automated the process by using docker-compose.yml file. Inside build stanza in the yml file, we provided the path to the Dockerfile for each service. Now when we run the docker-compose cmd, it will also build the images for each services as well.


Some good commands

```
docker inspect containerID-or-name
docker network
docker exec -t containerName bash
docker image ls
docker container ls
docker service ls
docker-machine ls
docker node ls
docker run -p 7000:9000 imageName

-p (port-to-expose : port-Where-NodeJS-listens)



docker build -t demo .   --> builds an image called demo


docker run command creates a container. Container is a running image.

docker run --rm -it demo  --> run the image i.e create container and get shell access to that image (rm is for removing the container upon exit)

docker image rm -f demo  --> remove the image

```

