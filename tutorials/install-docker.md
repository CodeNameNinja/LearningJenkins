## Instructions

[offical install docs](https://docs.docker.com/engine/install/centos/)

### Installation

1) `sudo yum install -y yum-utils`
2) ```bash
   sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo    

#### Install Docker Enginer

3) `sudo yum install docker-ce docker-ce-cli containerd.io`

4) `sudo systemctl start docker`
5) `sudo systemctl enable docker`
6) `docker ps` <- To test

> You should get an error from the above command, complaining about permission to connect

to resolve this we simply type out

7) `sudo usermod -aG docker <username>`

8) Logout and Log back in