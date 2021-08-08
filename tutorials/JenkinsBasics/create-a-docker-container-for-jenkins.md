## Instruction for setting and building a docker container for jenkins

First we need to get the proper permissions for Jenkins so Jenkins can write and read to the correct folder

To do that we can follow these instructions in our Linux Server:

1) `id`
2) Get uid of user e.g `1000`
3) `sudo chown 1000:1000 jenkins_home -R`

now verify with typing
`ll`

if you server is not running already type out

`docker-compose up -d`

and verify with `docker ps`

to get the logs we type out: 

`docker logs -f <container-name>`

 > get container name with `cat docker-compose.yml`

Now we need to get the IP address of our LINUX server. 

- `ip a` or get it from PUTTY

We want to hit this address in our browser but remember to append the port number to end: it should be by default on port `8080`

We should see a page like so:

![Jenkins Default Login Page](https://i.ibb.co/G7tmKst/Jenkins-Server.png)

Great! Now we need to get the password. 

Simply get it from typing `docker logs -f jenkins`

and we should see a bunch of information. copy the password where it mentioned the password in the terminal and paste in the browser where prompted.

Once pasting in correct password and hitting enter or 'proceed' 

we should see a screen like this

![Jenkins Success Page](https://i.ibb.co/4K0cgfC/Jenkins-Success-Login.png)

Now I would recommend to install the `Suggested Plugins`

Wait for the installation to be complete. Afterwards you should immediately see this screen

![Jenkins Create User Page](https://i.ibb.co/yfxK204/jenkins-create-user.png)

Fill in the form and hit *Proceed*

Afterwards we should see a screen like below: 
- Keep default

![Jenkins Instance Configuration](https://i.ibb.co/h92GLzb/Jenkins-Instance-Configuration.png)

Procceed past the next screen and you should see the Jenkins Dashboard page

![Jenkins Dashboard Page](https://i.ibb.co/XFgQXgp/Jenkins-Dashboard-Page.png)
