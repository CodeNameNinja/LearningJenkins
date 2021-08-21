### How to SSH into a remote server PT2 

#### Creating an ssh key

`ssh-keygen -f remote-key`

![SSH-Key](https://i.ibb.co/JsLY9zs/SShKey.png)

this generate two keys

`remote-key`

& 

`remote-key.pub`

We keep the private key secure and we use the public key on the server.

let's copy the public key to the server, so let's modify our `Dockerfile`

```bash

FROM centos:7

RUN yum -y install openssh-server

RUN useradd remote_user && \
    echo "1234" | passwd remote_user  --stdin && \
    mkdir /home/remote_user/.ssh && \
    chmod 700 /home/remote_user/.ssh

COPY remote-key.pub /home/remote_user/.ssh/authorized_keys

RUN chown remote_user:remote_user   -R /home/remote_user && \
    chmod 400 /home/remote_user/.ssh/authorized_keys

RUN ssh-keygen -A

CMD /usr/sbin/sshd -D

```

We install the server.
We configure out user with a password with a home folder.
And a ssh folder and we give permissions and we copy the public key that we generated.

We are generating some keys for SSH And then here we're just instructing Docker how the service should
be started.

And that's pretty cool.