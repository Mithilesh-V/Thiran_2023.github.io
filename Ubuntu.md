### Installing Docker on Linux: 

*Docker was built based on linux*

1. **Convenience script **

```shell
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
```

2. **Manual installation (Ubuntu 20.04)**

```shell
$ sudo apt-get update
$ sudo apt-get install \ apt-transport-https \ ca-certificates \ curl \ gnupg \ lsb-release

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

$ echo \ "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive keyring.gpg] https://download.docker.com/linux/ubuntu \

$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```shell
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

**Verify installation**
```shell
$ docker --version
$ docker run hello-world
```

*To run docker as non-root user*
```shell
$ sudo usermod -aG docker <NAME>
```
