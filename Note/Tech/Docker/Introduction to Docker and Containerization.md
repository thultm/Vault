# 1. Docker Overview
## 1.1 What is Docker?
> Docker is a platform for developing, shipping, and running applications. It enables software to be packaged into containers-standardized executable components combining application source code with the operating system (OS) libraries and dependencies required to run that code in any environment. ![](https://i.imgur.com/uOmZVP7.png)
## 1.2 Who use Docker?
- Used by a range of professionals, including:
- Software developers
- System administrators
- IT operations teams
- It's also popular in DevOps practices
## 1.3 **When was Docker created?**
- Docker was introduced in March 2013. 
- It has since evolved and gained significant popularity in the IT and software development communities, revolutionizing container-based virtualization.
## 1.4 **Where is Docker used?**
- Docker is used in various environments, from local development machines to production servers. 
- It's widely used in cloud computing environments and is supported by major cloud providers. 
- Docker can be found in small startups to large enterprises and across numerous industries.
## 1.5 **Why is Docker important?**
- Docker simplifies the process of managing applications in containers. 
- It resolves the common issue of "it works on my machine" by ensuring consistency across multiple development, testing, and production environments. 
- It also enhances resource utilization, reduces overhead, and makes it easier to scale and deploy applications.
## 1.6 **How does Docker work?**
- Docker uses containerization technology to create, run, and manage containers. A container is a lightweight, standalone package that includes everything needed to run a piece of software: code, runtime, system tools, and libraries. Docker containers are isolated but can communicate with each other through defined channels. The core components of Docker include:
	- **Docker Engine**: The runtime that builds and runs containers.
	- **Docker Images**: Read-only templates used to build containers.
	- **Docker Containers**: Runnable instances of Docker images.
	- **Docker Hub/Registry**: A service for hosting and sharing Docker images.
	- **Dockerfile**: A script containing instructions to build a Docker image.
	- **Docker Compose**: A tool for defining and running multi-container Docker applications.
## 1.7 Docker architecture 
- Docker uses a client-server architecture
![](https://i.imgur.com/MS8kqSf.png)
### 1.7.1 The Docker daemon
- The Docker daemon (`dockerd`) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. 
- A daemon can also communicate with other daemons to manage Docker services.
### 1.7.2 The Docker client
- The Docker client (`docker`) is the *primary way* that many Docker users interact with Docker. 
- When you use commands such as `docker run`, the client sends these commands to `dockerd`, which carries them out. 
- The `docker` command *uses the Docker API.*
- The Docker client *can communicate with more than one daemon.*
### 1.7.3 Docker Desktop
Docker Desktop includes the Docker daemon (`dockerd`), the Docker client (`docker`), Docker Compose, Docker Content Trust, Kubernetes, and Credential Helper.
# 2. Container
## 2.1 What is Container?
> A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. A Docker container image is a *lightweight, standalone, executable package of software that includes everything needed to run an application*: code, runtime, system tools, system libraries and settings. ![](https://i.imgur.com/HsODns9.png)
- Docker Containers Are Everywhere: Linux, Windows, Data center, Cloud, Serverless, etc. ![](https://i.imgur.com/coW9r2C.png)
- Comparing Containers and Virtual Machines: Containers are more portable and efficient. ![](https://i.imgur.com/rRAX41A.png)
## 2.2 Who uses Containers?
- Containers are used by 
- Software developers 
- System administrators 
- DevOps professionals 

They are widely adopted in organizations that implement microservices architectures, as they facilitate the development, deployment, and scaling of applications.
## 2.3 When should Containers be used?
- Containers are suitable when you need:
	- *Consistency* across multiple development, testing, and production environments.
	- *Rapid deployment, scaling, and version control* of applications.
	- *Running multiple* applications *on the same server* efficiently.
	- *Easy and fast replication* of environments and application configurations.
	- *Isolation of applications* for security and performance reasons.
## 2.4 Where are Containers used?
- Containers can be used in various environments, including:
    - Local development machines.
	- Testing environments.
	- Production environments, both on-premises and in the cloud.
- They are *platform-independent* and can be run on any computer, on any infrastructure, and in any cloud.
## 2.5 Why are Containers important?
- Containers *provide a consistent environment* for applications from development through production, easing the CI/CD (Continuous Integration/Continuous Deployment) pipeline.
- They *isolate applications and their dependencies* from the underlying infrastructure.
- Containers offer a lightweight alternative to full machine virtualization, requiring fewer resources, which means more applications can run on the same hardware.
## 2.6 How do Containers work?
- Containers run on a container engine (like Docker or rkt).
- They *use the host operating system's kernel but create isolated environments for running applications.*
- Unlike virtual machines, containers do not bundle a full operating system-only the minimum necessary components.
- They allow applications to be isolated from each other and the host system, but share the same OS kernel, which makes them more efficient, faster, and less resource-intensive compared to running full virtual machines.
# 3. Docker vs VM
|FEATURE|DOCKER|VIRTUAL MACHINE (VM)|
|---|---|---|
|Compatibility|Works best with Linux distributions|All operating systems|
|Size|Light in weight|Substantially larger – of the order of Gigabytes or more|
|Virtualization|Only the applications layer|Both the OS kernel and applications layers|
|Performance|Easy to start containers (typically takes milliseconds)|Takes longer to start a VM instance|
|Security|Less secure|Relatively more secure|
|Replicability|Easy to replicate. You can pull Docker images corresponding to the various applications|Difficult to replicate, especially with increasing number of VM instances|
