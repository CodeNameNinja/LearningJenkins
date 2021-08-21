### Finish Configuration for your SSH server

lets edit our docker-compose file again with 

`vi docker-compose.yml`

and let us make a few changes. 

Firstly we need to create your new service `remote-host` and specify the image, we can name it what we like as we are going to make our own image, so for example I chose `remote-host`, and we need to specify the `build` `context` in our case that would be in your container called `centor7`


and then lastly add it to the network as we did with our jenkins service.

```bash

version: '3'
services:
  jenkins:
    container_name: jenkins
    image: jenkins/jenkins
    ports:
      - '8080:8080'
    volumes:
      - "$PWD/jenkins_home:/var/jenkins_home"
    networks:
      - net
  remote_host:
   tty: true
   container_name: remote-host
   image: remote-host
   build:
    context: centos7
   networks:
      - net
networks:
  net:

```

lets build it!

`docker-compose build`

if everything is correct, we should see a message like this:

![Build Succesfull remote-host:latest](https://i.ibb.co/6FmnDCP/Screenshot-2021-08-20-123242.png)

To verify this, we can use `docker image` and you should see our newly created docker image

![Docker image: remote-host](https://i.ibb.co/wYqjgF3/Screenshot-2021-08-20-123518.png)

Great!

Now lets spin up the containers with 

`docker-compose up -d`

and we should see both remote-host and jenkins contains running.

now lets get into our jenkins container and ssh into our remote_host container

> first get into bash in remote_host if you get permissions errors and remove this file
> ```bash
> ls -l /run/nologin
> rm /run/nologin
> ```

`docker exec -ti jenkins bash`

and then connect to remote host with our remote_user

```bash
ssh remote_user@remote_host
```
and type `yes` to allow ssh key to be added to known hosts.

lets verify that we can connect to our remote_host from our jenkins container.

`exit`
and we should be back to our normal directory. lets go into our `centos7` directory and copy our remote-key to our jenkins containers.

`docker cp remote-key jenkins:/tmp/remote-key`

lets get into your jenkins container by running
```bash
docker exec -it jenkins /bin/bash

cd tmp/


```

![remote-key in tmp folder](https://i.ibb.co/SNHGZv6/Screenshot-2021-08-21-173949.png)

now let's use it:

```bash
ssh -i remote-key remote_user@remote_host
```

and we should be able to log in without any password.