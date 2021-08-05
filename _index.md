# Getting started on Docker

#### Nishanth Gobi

## What is Docker?
> An open source containerization technology for building and containerizing your applications.

## Why do we need docker?

Up until a few years back, software companies would often face the issue of **mismatches in dependencies/libraries** between the development team and testing team. And docker was developed to solve this problem while addressing the drawbacks of hypervisors. 

**How do we solve this?**

1. JAR files 
	-  **Java ARchive** is a package file format typically used to aggregate many Java class files and associated metadata and resources (text, images, etc.) into one file for distribution. 
	- Drawback: Extra dependencies that even the developer is not aware of!
		
2. Hypervisor 

 	- Hypervisors are basically VMs.
	- With hypervisors, softwares can be developed on the guest OS (VM) and it can be shipped off as a whole image along with all the dependencies.
	- *"Like instances of a class object"*


<center><table>
<tr><td>Guest OS</td><td>Guest OS</td><td>Guest OS</td></tr>
	<tr><td colspan="3"> Hypervisor </td></tr>
<tr><td colspan="3"> <i>(Host OS)</i> </td></tr>
	<tr><td colspan="3"> Hardware </td>	</tr>
</table></center>

**Drawbacks with hypervisors**
- VMs are heavy! Hence, we cannot run many Guest OSs simultaneously.
- OS licensinng

3. Containers

	- Loosely isolated environments
	- Overcomes the disadvantages of Hypervisor
	- Idea origin: *LXE* (Linux containers)
	- Containers share the same os


<center><table>
<tr><td>App 1</td><td>App 2</td><td>App 3</td></tr>
<tr><td colspan="3"> <i>Docker</i> </td></tr>
<tr><td colspan="3"> <i>OS</i> </td></tr>
	<tr><td colspan="3"> Hardware </td>	</tr>
</table></center>


**& that's why we need Docker!**

Docker helps pack your apps along with it's dependencies into a single container and the image of the container can then be shared with others.


## Installation

[Try Docker before installing](http://labs.play-with-docker.com)

[Ubuntu](/content/Ubuntu.md)

[Windows](/content/Windows.md)


## Basic Docker commands

Check docker status:
```shell
sudo systemctl status docker
```

List all containers:
```shell
sudo docker ps -a
```
```shell
sudo docker container ls -a
```

List all docker image:
```shell
sudo docker image ls
```
```shell
sudo docker images
```

Remove a docker container:
```shell
sudo docker rm <CONTAINER_ID>
```

Remove a docker image:
```shell
sudo docker rmi <IMAGE_ID>
```
*If you want to remove an image you have to remove all the containers that use the image first!*

Pull an image from Docker hub:
```shell
sudo docker pull <IMAGE_NAME>
```

 > What happens when you pull a docker image?
> 1. Checks for the image in your local repo
> 2. If not found, then checks for the image in docker hub and downloads it 
> 3. Makes a container with the image

## Sample 

[Running Ubuntu on docker](Docker/'Running Ubuntu on Docker.md')


## Docker Engine

**Docker engine** - The software that you have installed in your system

 <img src="https://wiki.aquasec.com/download/attachments/2854889/Docker_Engine.png?version=1&modificationDate=1520172702424&api=v2">

### Components

1. Images 
> Read-only binary templates used to create Docker containers.

2. Container
> A container is a runnable instance of an image. You can create, start, stop, move, or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.

3. Networking
> Docker implements networking (between containers and host) in an application-driven manner. 
>List of available drivers: 
>- Bridge (default) 
>- Host 
>- None 
>- Overlay (Swarm services) 
>- Macvlan

4. Data Volumes
> Once you destroy a container all the data in it is lost.
> We use data volumes to store data from docker containers. 


### Docker Architecture

- Docker uses a **client-server** architecture 
- The __Docker client__ talks to the __Docker daemon__, which does the heavy lifting of building, running, and distributing your Docker containers. 
- The Docker client and daemon communicate using a __REST API__
- Thus the client and daemon can run on the same system, or you can connect the client to a remote Docker daemon. 

<img src="https://docs.docker.com/engine/images/architecture.svg">


## How to use docker?

1. You can [Dockerise Apps](content/'Dockerise Apps.md') that have already been developed.
2. You can [Create App in docker](content/'Create App in docker.md').


## Got dockerised??
Learn more at [Docker Docs](https://docs.docker.com/)