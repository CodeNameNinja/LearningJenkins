## How to create and use a Bash script in Jenkins and

To create a script use

> `vi <script-name>.sh`

To start typing press the letter 

> `i`

first line should be what interpreter we are going to use

>`#!/bin/bash`

let's try and echo out a Name and surname. 

`echo "Hello, $NAME $LASTNAME"`

hit `esc` and type `wq` to save and exit.

lets try and run it like so:

`./scripts.sh`

we should be greeted with an error message: 

```bash
-bash: ./script.sh: Permission denied
```

okay, lets grant the permsiion with

```bash
chmod +x ./script.sh
```

This will give us executable permissions to the file.

now lets try and run it again and we should see

```bash
./script.sh

Hello,
```

Let's try and accept parameters for name and LASTNAME


```bash
#!/bin/bash

NAME=$1
LASTNAME=$2

echo "Hello, $NAME $LASTNAME"

```

this is how we can accept parameters when running the scripts
```bash
./script.sh Mitchell Yuen


Hello, Mitchell Yuen
```

### Executing the file in Jenkins

In the future we will take a look at using `Volumes` to share folders between the container and the host. 

But for now we will just copy the script file into our container

`docker cp script.sh jenkins:/tmp/script.sh`


![Docker CP](https://i.ibb.co/D1MyN84/bash-script.png)

lets copy the path of the script `/tmp/script.sh` and go to jenkins and into our `job`

![running script.sh](https://i.ibb.co/MSC1xQD/script-sh2.png)

Let's hit `Save` and `Build`

![Build Output](https://i.ibb.co/BV53QY7/output-script-sh.png)