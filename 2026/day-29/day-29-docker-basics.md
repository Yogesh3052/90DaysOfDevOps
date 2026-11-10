## What is a container and why do we need them?
### ANS: container is the lightweight executible package which bundles all the code, runtime, system libraries,dependency together.
### containers solve the problem of "it runs on my machine but not yours". Containers are portable. It can run on different environment without any issue. Each container runs isolated means it does not interfere with host system.

## Containers vs Virtual Machines — what's the real difference?
### the main difference is that container run on the kernel of host machine and virtual machine run on the hypervisor of host machine. due to this containers are lightweight as compared to virtual machine. The isolation of the virtual machine is much stronger than container. 

## What is the Docker architecture? (daemon, client, images, containers, registry)
###
1. 🐳 The Docker Daemon (dockerd)

The daemon is the brain of Docker. It is a persistent background process that runs on the host machine.
• Role: It listens for Docker API requests and manages Docker objects.
• Responsibilities: It handles the entire lifecycle of your infrastructure, including creating images, managing containers, handling networks, and configuring storage volumes.

2. 🖥️ The Docker Client (docker)

The client is the primary user interface that you interact with.
• Role: When you type a command like docker run or docker build into your terminal, the client translates it.
• Mechanism: It sends these commands as REST API requests over UNIX sockets or a network interface directly to the Docker Daemon. A single client can easily communicate with a remote daemon on a completely different machine.

3. 💾 Docker Images

An image is a read-only blueprint used to build a container.
• Role: It contains the application code, libraries, tools, and configurations your app needs to run.
• Structure: Images are built in immutable, cached layers using instructions written in a Dockerfile. Because layers are reusable, if you update one part of your app, Docker only rebuilds the modified layer.

4. 📦 Docker Containers

A container is a runnable, isolated instance of a Docker Image.
• Role: If the image is the "recipe," the container is the "dish" you cooked from it.
• Mechanism: When you launch a container, Docker adds a thin, writable layer on top of the read-only image layers. Containers use underlying Linux kernel technologies (like namespaces for process isolation and cgroups for resource limits) to run completely isolated from the host and other containers.

5. 🌐 Docker Registry

A registry is a centralized storage warehouse for sharing and distributing Docker images.
• Role: It is the platform where you save your images or download pre-made ones.
• Types: Docker Hub is the default, public registry that Docker automatically looks at. However, companies often set up private registries (like AWS ECR or GitHub Packages) to secure proprietary application code.


