## Run Ubuntu in docker

Get the image
```shell
sudo docker image pull ubuntu:latest
sudo docker image ls
```

Run the container 
```shell
sudo docker run -it {IMAGE_ID} {COMMAND}
sudo docker run -it {IMAGE_ID} /bin/bash
```

Check with shell commands
```shell
ls
who
```

```shell
ping google.com
apt get install iputils-ping
```