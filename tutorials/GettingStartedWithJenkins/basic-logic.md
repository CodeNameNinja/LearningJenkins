## How to use an `If` statement

Let's add a third Parameter called `SHOW_NAME`. 

This parameter will determine wether we display the name or show an error. 

```bash
#!/bin/bash

NAME=$1
LASTNAME=$2
SHOW_NAME=$3

if [ "$SHOW_NAME" = "true" ]; then
 echo "Hello, $NAME $LASTNAME"
else
 echo "Enable SHOW_NAME to see output"
fi
```
copy this script to the container like so:

`docker cp script.sh jenkins:/tmp/script.sh`

Add a boolean paremeter to your job in jenkins and apply it in the execute script

![Boolean param](https://i.ibb.co/7z2dPRg/boolean-param-2.png)
![Boolean param](https://i.ibb.co/17P28GS/boolean-param.png)

Try and build it with parameters, and see the output.