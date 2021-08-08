## Instructions for Docker Compose file management

1) `mkdir jenkins`
> `pwd`   
> `/home/jenkins/`
2) `cd jenkins`
3) `vi docker-compose.yml`

4) copy and paste the following.
```yml
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
networks:
  net:
```

5) `esc`  type: `wq`

verify that it saved

6) `cat docker-compose.yml`

7) `mkdir jenkins_home`

8) `docker-compose up -d`

> that will spin the jenkins server in detached mode