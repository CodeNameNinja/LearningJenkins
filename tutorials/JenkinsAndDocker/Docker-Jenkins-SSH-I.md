### How to SSH into a remote server.

#### What happens if we want to run jobs on a remote server?

Let's find out by creating one. we have two options for this demo, we can spin up another virtual machine or we can just create another container in our current server and have an SSH service, we will go with the second option.


Let's create another folder and inside we will install a centos7 container.

`mkdir centos7`

and let's create a Docker file

`vi Dockerfile`

In side type out or copy and paste the following

```bash
FROM centos

RUN yum -y install openssh-server

RUN useradd remote_user && \
    echo "remote_user:1234" | chpasswd && \
    mkdir /home/remote_user/.ssh && \
    chmod 700 /home/remote_user/.ssh

```

essentially this will create a new user in our centos7 container and give them a password of 1234 and create a folder for their .ssh directory and give them permissions to it.