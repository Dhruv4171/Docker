## Docker Overview

**Docker** is an open-source platform that simplifies application deployment by packaging applications and their dependencies into isolated environments called **containers**. These containers ensure consistent behavior across different systems, addressing the common problem of "it works on my machine."

---

### Key Concepts:

1. **Base Image**:  
   The foundational layer for creating custom Docker images. Examples include operating systems (e.g., *Ubuntu*) or language runtimes (e.g., *Python*).

2. **Dockerfile**:  
   A script defining the steps to build a Docker image. It typically includes:
   - The **base image** (e.g., Ubuntu).
   - Application code and dependencies.
   - Configuration steps (e.g., environment variables).

3. **Docker Image**:  
   A read-only package containing all the components necessary to run an application (code, libraries, dependencies). Images serve as templates for containers.

4. **Docker Container**:  
   A running instance of a Docker image, providing an isolated environment to execute applications. Containers are lightweight and portable.

5. **Virtual Machine (VM) vs. Docker Container**:
   - **Weight & Size**: Containers share the host OS kernel, making them smaller and more resource-efficient compared to VMs, which require a full OS.
   - **Start Time**: Containers start in seconds, while VMs take longer due to OS boot-up.
   - **Resource Efficiency**: Containers share system resources, whereas VMs consume more resources by running their own OS.

---

### Docker Components:

1. **Kernel**:  
   The core of an OS, managing hardware interactions, memory, processes, and system calls.

2. **Docker Daemon (`dockerd`)**:  
   A background service managing Docker containers, images, networks, and volumes. It listens for API requests to perform operations.

3. **Docker Engine**:  
   The core component of Docker, comprising the daemon, REST API, and Docker CLI (command-line interface).

4. **WSL (Windows Subsystem for Linux)**:  
   Allows Linux distributions to run on Windows without a virtual machine, facilitating development with Linux-based tools in a Windows environment.

---

### Basic Docker Commands:

#### System Information:
- **Check Docker Info**:  
   ```bash
   docker info
   ```  
   Displays system-wide information about Docker.

#### Image Management:
- **List Docker Images**:  
   ```bash
   docker images
   ```  
   Lists all available Docker images on your system.

- **Search for an Image on Docker Hub**:  
   ```bash
   docker search python
   ```  
   Searches for Python-related images on Docker Hub.

- **Download an Image from Docker Hub**:  
   ```bash
   docker pull hello-world
   ```  
   Pulls the `hello-world` image from Docker Hub.

- **Download a Tagged Image**:  
   ```bash
   docker pull python:3.9.20-slim
   ```  
   Pulls a specific version of a Python image.

#### Container Management:
- **Create and Run a New Container**:  
   ```bash
   docker run hello-world
   ```  
   Creates and runs a container from the `hello-world` image.

- **Create and Name a Container**:  
   ```bash
   docker run --name hellocontainer hello-world
   ```  
   Assigns the name `hellocontainer` to the new container.

- **Run a Container in Detached Mode**:  
   ```bash
   docker run --name python_container_2 -d python:3.9.20-slim
   ```  
   Runs the container in the background (detached mode).

- **Run in Interactive and Detached Mode**:  
   ```bash
   docker run --name python_container_3 -it -d python:3.9.20-slim
   ```  
   Starts an interactive terminal session with the container while running it in the background.

- **Create and Remove a Temporary Container**:  
   ```bash
   docker run --name python_container_4 -it --rm python:3.9.20-slim
   ```  
   Automatically removes the container after it stops.

#### Container Lifecycle:
- **Stop, Start, and Restart a Container**:
   - Stop a container:  
     ```bash
     docker stop python_container_3
     ```
   - Start a container:  
     ```bash
     docker start python_container_3
     ```
   - Restart a container:  
     ```bash
     docker restart python_container_3
     ```

#### Container Logs & Inspection:
- **View Container Logs**:  
   ```bash
   docker logs <container_name>
   ```  
   Displays the logs of the specified container.

- **Inspect a Container**:  
   ```bash
   docker inspect <container_name_or_id>
   ```  
   Provides detailed information about a container or image.

#### Container Cleanup:
- **Remove a Container or Image**:
   - Remove a container:  
     ```bash
     docker rm <container_id>
     ```
   - Remove an image:  
     ```bash
     docker rmi hello-world
     ```
   Note: You cannot remove an image that is still in use by a container.

- **Remove All Stopped Containers**:  
   ```bash
   docker container prune
   ```  
   Deletes all stopped containers.

- **Prune Docker System Resources**:  
   ```bash
   docker system prune
   ```  
   Cleans up unused containers, networks, images, and optionally, volumes.

- **Prune Docker Images**:  
   Remove unused or dangling images:
   - **Dangling images**:  
     ```bash
     docker image prune
     ```
   - **All unused images**:  
     ```bash
     docker image prune -a
     ```

---

### Detached vs. Non-Detached Mode:
- **Detached Mode (`-d`)**:  
   Runs containers in the background, freeing up the terminal.
- **Non-Detached Mode**:  
   Runs containers in the foreground, requiring the terminal to remain open.
