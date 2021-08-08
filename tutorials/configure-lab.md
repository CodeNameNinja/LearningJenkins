
# Configure Lab

This section will go through the following:

- Install and setup Centos on Virtual box
- Install Docker and Docker Compose
- Pull jenkins image
- Setup Putty for SSH into our Jenkins Server. 
- Create a Jenkins Compose file and configuration

## Install and Setup CentOS 

Firstly install Virtual Box which would be the service that we will be using to create a Virtual Machine(VM)
[Virtual Box](https://www.virtualbox.org/wiki/Downloads)

Then install a minimal ISO version of CentOS 7
[CentOS 7.x](https://www.virtualbox.org/wiki/Downloads)

1) Open VirtualBox and click on *New*. 
2) Name it whatever you want e.g `jenkins`
3) select the type to be `Linux`
4) and the Version to be `Red Hat 64 bit`
5) hit next and allocate memory e.g `2048mb`
6) Keep selection at `Create a virtual hard disk now`
7) Click `Create` and then keep selection at `VDI`
7) Keep `Dynamically allocate`
8) Choose Storage capacity i.e `20GB`

We have created our `Linux VM`

We then want to head into the settings of our newly created VM and change the network settings. 

so as the following: 

1) Click on `Settings`
2) Click on `Network`
3) Change Adapter to `Bridged Adapter`
4) Select the name to either Ethernet or Wireless, which ever you prefer.

Okay now we have the base setup done, lets hit `Start` and wait for the VM to boot up. 

You should get a prompt that asks to select start up disk, we can now select the `CentOS` ISO we downloaded earlier. 
and then hit *start* 

1) Use the arrows and `enter` to select `Install CentOS 7`
2) Choose Language.
3) Select Installation Desitination. 
4) Make sure that Partioning is `Automatic` and click on `Done`
5) Click on the Network & Host Name. 
6) Turn the Ethernet Adapter on. 

> This will show an IP address if all is correct. we will use this IP Address to SSH later from PUTTY.

7) Click `Begin Installation`
8) Setup Root Password and Admin User.
9) Wait until the Installation is completed.
10) Hit `Reboot`

Great our machine is completly setup and we can now start setting up `Jenkins`

Now we can login with the details that we created earlier. 
get the Ip address

`ip a`

`192.168.1.158`

Download [Putty](https://www.putty.org/)

Configure the IP address that we got from the previous step and hit enter

> You can save this so you don't have to repeat this step each time.


