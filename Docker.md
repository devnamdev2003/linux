<h1 style="text-align: center;">DOCKER</h1>

## Topic:

1. [Commands](#commands)
2. [Tracking_docker_containers](#tracking_docker_containers)


## Commands

1. **Pull an Image:**
   - Pull a Docker image from Docker Hub.
     ```bash
     docker pull image_name:tag
     ```
   
2. **List Images:**
   - List all Docker images on your system.
     ```bash
     docker images
     ```

3. **Run a Container:**
   - Run a Docker container based on an image.
     ```bash
     docker run -it image_name:tag
     ```

4. **List Running Containers:**
   - List all running Docker containers.
     ```bash
     docker ps
     ```

5. **List All Containers:**
   - List all Docker containers (including stopped ones).
     ```bash
     docker ps -a
     ```

6. **Stop a Container:**
   - Stop a running Docker container.
     ```bash
     docker stop container_id_or_name
     ```

7. **Remove a Container:**
   - Remove a Docker container.
     ```bash
     docker rm container_id_or_name
     ```

8.  **Remove an Image:**
   - Remove a Docker image.
     ```bash
     docker rmi image_id_or_name
     ```

9.  **Build an Image from a Dockerfile:**
   - Build a Docker image from a Dockerfile.
     ```bash
     docker build -t image_name:tag .
     ```

10. **Inspect Container Details:**
    - View detailed information about a Docker container.
      ```bash
      docker inspect container_id_or_name
      ```

11. **View Container Logs:**
    - View the logs of a running Docker container.
      ```bash
      docker logs container_id_or_name
      ```

12. **Execute a Command in a Running Container:**
    - Run a command inside a running Docker container.
      ```bash
      docker exec -it container_id_or_name command
      ```

13. **Attach to a Running Container:**
    - Attach to a running Docker container's console.
      ```bash
      docker attach container_id_or_name
      ```

14. **Create a Docker Network:**
    - Create a user-defined Docker network.
      ```bash
      docker network create network_name
      ```

15. **List Docker Networks:**
    - List Docker networks.
      ```bash
      docker network ls
      ```

16. **Remove a Docker Network:**
    - Remove a Docker network.
      ```bash
      docker network rm network_name
      ```

17. **Volume Management:**
    - Create a Docker volume.
      ```bash
      docker volume create volume_name
      ```

    - List Docker volumes.
      ```bash
      docker volume ls
      ```

    - Remove a Docker volume.
      ```bash
      docker volume rm volume_name
      ```

These commands cover some of the basic Docker operations. Depending on your use case, you might need additional commands and options. Always refer to the Docker documentation for comprehensive information about each command and its options.


---



## Tracking_Docker_containers
Here are some commands and approaches to track Docker containers:

### 1. **Check Container Status:**

To see the current status of your Docker containers, you can use the following command:

```bash
docker ps
```

This command shows a list of running containers along with their details. If you want to see all containers, including those that are stopped, use:

```bash
docker ps -a
```

### 2. **View Container Logs:**

To view the logs of a specific container, you can use the `docker logs` command. For example:

```bash
docker logs my_container_name
```

Replace "my_container_name" with the actual name or ID of your container.

### 3. **Monitor Resource Usage:**

Docker provides the `docker stats` command to monitor resource usage of running containers in real-time. It shows CPU, memory, and network usage. Example:

```bash
docker stats my_container_name
```

### 4. **Inspect Container Details:**

To get detailed information about a container, including its configuration and network settings, you can use the `docker inspect` command:

```bash
docker inspect my_container_name
```

### 5. **Track Container Events:**

Docker logs events related to containers. You can view these events using the `docker events` command. This can be useful for tracking container lifecycle events:

```bash
docker events
```

### 6. **Attach to Container:**

You can attach to a running container's console to interact with it in real-time. Use the following command:

```bash
docker exec -it my_container_name /bin/bash
```

Replace "my_container_name" with the actual name or ID of your container.

### 7. **Health Checks:**

If your Docker image includes health checks, you can use the `docker inspect` command to see the health status. Look for the `"Health"` section:

```bash
docker inspect --format='{{json .State.Health}}' my_container_name
```

### 8. **Container Stats with Specific Metrics:**

Docker also provides the `docker stats` command with additional options to display specific metrics. For example, to display only the CPU usage, you can use:

```bash
docker stats --format "table {{.Name}}\t{{.CPUPerc}}"
```

These commands and approaches give you various ways to track and monitor your Docker containers. Choose the method that best suits your needs and the specific information you are looking for.