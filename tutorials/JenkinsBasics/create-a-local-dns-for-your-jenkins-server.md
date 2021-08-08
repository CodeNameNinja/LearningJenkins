## Instructions for creating a local DNS for your Jenkins Server

1) Open Notepad as Administrator
2) Click on File > Open
3) Windows(c:) > Windows > System32 > drivers > etc
4) Select filter for all files
5) and open the hosts file.
6) Copy the IP address of your Jenkins Server 
   > `ip a` or get it from PUTTY
7) Then add it to your hosts and name it what your like, I named it `jenkins.local`

![Hosts](https://i.ibb.co/gyfd7CJ/Hosts.png)

then navigate to your browser and type in

`<host-name>:8080`

![Jenkins.local](https://i.ibb.co/bLwbctD/jenkins-local.png)