# Chapter 2: Containers in Action with Podman  

## Objective:  

By the end of this chapter, you should be able to run, interact with, inspect, and manage containers using Podman.

## 2.1. Running Your First Container  

### Fetching and Running a Container  

**Container Registry**

A container registry is a place where container images are stored and distributed. It's much like an app store but for containers. When you need to run a particular container, you pull the image from a registry. Some popular container registries include Docker Hub, Quay.io, and the Google Container Registry.  

There are two main types of registries:

* Public Registries: These are open for everyone. Anyone can pull images from them. Examples include Docker Hub and Google's gcr.io for public repositories.  
* Private Registries: These are restricted and require authentication to pull or push images. Organizations use private registries to store proprietary apps or for security reasons.

*Analogy:*

>Imagine you're cooking and you need a specific type of sauce. You could make it from scratch, or you could go to the store (registry) and buy a pre-made one (pull an image). The store has a variety of sauces (images) stored on its shelves, ready to be picked up. Some special sauces might be behind a counter (private registry) and you'd need a membership card (authentication) to buy them.

![](../images/sauces.png)  

**Exercise:**  Pulling an Image using Podman    
Inspecting Available Images:  
Before we pull an image, let's first check what images we already have on our system.

`podman images` 

Pulling an Image:  
Now, let's pull the nginx image from the Docker Hub registry.  

`podman pull nginx` 

This command fetches the nginx image from Docker Hub and saves it to our local system.

Verifying the Image:  
After the pull operation, we should verify that the image is now available locally.  

`podman images` 

You'll now see the nginx image listed, indicating that it has been successfully pulled from the registry and is ready to be run as a container.  

To start off, let's fetch and run a basic container:  

`podman run -it --rm docker.io/library/alpine:latest /bin/sh` 

This command pulls the alpine:latest image (if it doesn't exist locally), creates a container from it, and runs */bin/sh* inside the container.  

* **run**: Tells Podman to create a new container.  
* **-it**: Stands for "interactive terminal," allowing you to interact with the container.  
* **--rm**: Removes the container after it's done running.  
* **docker.io/library/alpine:latest**: Specifies the image to use.  

Once inside the container, try out a few basic commands:  
```bash
echo "Hello from inside the container!"
cat /etc/os-release
```  
### Exiting the Container  

You can exit the container by typing exit.  

## 2.2. Inspecting Containers  

### Viewing All Running Containers  

`podman ps` 

### Viewing All Containers (including stopped ones)  

`podman ps -a` 

### Getting Detailed Information about a Container  

`podman inspect <container_id>` 

## 2.3. Managing Containers  

### Starting and Stopping Containers  

To start a stopped container:

`podman start <container_id>`   

To stop a running container:  

`podman stop <container_id>`  

## 2.4. Networking with Containers  

Port Forwarding with Containers

Definition:

Port forwarding with containers means redirecting a communication request from one address and port number combination to another while the packets are traversing a network gateway, such as a router or firewall. In the context of containers, it allows us to access services running inside a container from our host or even from outside our host.

Why is it Important?

Containers are isolated by default, which means if a service is running inside a container on a specific port, it's not directly accessible from outside the container. Port forwarding allows us to bridge this gap, making containerized applications accessible.

How it Works with Podman:

When you run a container using Podman and specify a port to be forwarded, Podman sets up a network route that forwards traffic from a specified port on your host to a specified port on your container.

### Exposing Ports  

Let's run a basic HTTP server and expose its port:  

`podman run -d -p 8080:80 docker.io/library/httpd` 

Visit <your_instance_ip>:8080 in your browser to see the server in action.  

### Inspecting Network Settings

Inspect the network settings of a container:

`podman inspect <container_id> | grep IPAddress` 

## 2.5. Exercise

**Guided Exercise:**    
Run an NGINX container, expose its port 80 to your host's port 8081, and visit it through a web browser. Stop the container, inspect its network settings, and then remove the container.