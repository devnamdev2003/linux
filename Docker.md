<h1 style="text-align: center;">DOCKER</h1>

## Topic:

- [Topic:](#topic)
- [Commands](#commands)
- [The lifecycle of a Docker container](#the-lifecycle-of-a-docker-container)
- [Tracking Container Properties:](#tracking-container-properties)
  - [Updating Container Properties:](#updating-container-properties)
  - [Best Practices and Considerations:](#best-practices-and-considerations)


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

## The lifecycle of a Docker container

Docker container is a multi-stage process involving the creation, starting, execution, and eventual termination of a containerized application. Each stage is facilitated by specific Docker commands that enable users to manage and interact with containers seamlessly.

1. **Create:**
   - The first step in the lifecycle is the creation of a Docker container. The command responsible for this is `docker run`. When you issue a `docker run` command, you initiate the process of creating a new container instance based on a specified Docker image. The image serves as a blueprint for the container, encapsulating the application, its dependencies, and runtime environment. For instance:
     ```bash
     docker run -it --name my_container image_name
     ```
     This command instructs Docker to create and run a new container named "my_container" based on the specified image.

2. **Start:**
   - Once a container is created, it exists in a stopped state. To set it in motion, the `docker start` command is employed. This command transitions the container from a stopped state to a running state, making the encapsulated application accessible. An example would be:
     ```bash
     docker start my_container
     ```
     Here, "my_container" is started, and any processes defined within the container are initiated.

3. **Execute:**
   - While a container is running, users often need to interact with it or execute additional commands within its environment. The `docker exec` command facilitates this interaction by allowing users to execute commands inside a running container. For instance:
     ```bash
     docker exec -it my_container /bin/bash
     ```
     This command opens an interactive bash shell within the running container, providing a means to perform actions or troubleshoot.

4. **Pause/Unpause:**
   - Docker offers the ability to temporarily halt and resume the execution of a running container using the `docker pause` and `docker unpause` commands. When a container is paused, its processes are frozen, and when unpause, they resume. Examples include:
     ```bash
     docker pause my_container
     docker unpause my_container
     ```
     These commands provide a way to control the state of a container without stopping or restarting it.

5. **Stop:**
   - To gracefully stop a running container, the `docker stop` command is employed. This command sends a SIGTERM signal to the main process within the container, allowing it to perform cleanup before shutting down. For example:
     ```bash
     docker stop my_container
     ```
     The container transitions from a running state to a stopped state, and resources are freed up.

6. **Restart:**
   - The `docker restart` command combines the actions of stopping and starting a container. This is useful for applying changes or restarting a container without altering its configuration. An example would be:
     ```bash
     docker restart my_container
     ```
     This command halts the container and then starts it again, effectively restarting its processes.

7. **Remove:**
   - The `docker rm` command is used to completely remove a stopped container. This action deletes the container and releases associated resources. An example:
     ```bash
     docker rm my_container
     ```
     It's important to note that this command removes the container itself but does not delete the underlying Docker image.

8. **Inspect:**
   - For obtaining detailed information about a container, including its configuration, network settings, and more, the `docker inspect` command is employed. This command outputs a JSON-formatted result, offering insights into various aspects of the container. For instance:
     ```bash
     docker inspect my_container
     ```
     The information provided can be crucial for debugging, troubleshooting, or gaining a deeper understanding of the container's internals.

9. **Logs:**
   - The `docker logs` command allows users to view the logs generated by a container. This is particularly useful for monitoring and diagnosing issues within the containerized application. An example:
     ```bash
     docker logs my_container
     ```
     Log output may include application-specific messages, errors, or any other information deemed relevant.

10. **Kill:**
    - In scenarios where a container is unresponsive to the `docker stop` command, the `docker kill` command can be employed to forcefully terminate the container. This command sends a SIGKILL signal, terminating the container immediately. An example:
      ```bash
      docker kill my_container
      ```
      It's important to use this command judiciously, as it does not allow the container to perform cleanup before termination.

In essence, the Docker container lifecycle encapsulates the journey from creation to termination, with each command playing a distinct role in managing and interacting with containers. This comprehensive set of commands empowers users to effectively orchestrate containerized applications, ensuring seamless deployment, operation, and maintenance in the dynamic world of containerization. Understanding and mastering these commands are fundamental to harnessing the full potential of Docker containers in various development and deployment scenarios.


---


## Tracking Container Properties:

The lifecycle management of Docker containers involves a variety of commands and techniques, providing users with the ability to track and update container properties effectively. In this comprehensive guide, we'll explore the key commands and practices involved in tracking and updating Docker container attributes.

1. **Inspecting Container Details:**
   The `docker inspect` command serves as a powerful tool for retrieving detailed information about a container. By providing the container's name or ID, users can obtain an extensive JSON-formatted output encompassing essential details such as configuration, network settings, and more. This command is instrumental in understanding the current state and characteristics of a running or stopped container.

   Example:
   ```bash
   docker inspect my_container
   ```

2. **Viewing Container Logs:**
   Monitoring the output generated by a container is crucial for understanding its behavior and diagnosing potential issues. The `docker logs` command allows users to access the logs produced by a container, providing insights into application-specific messages, errors, and other relevant information.

   Example:
   ```bash
   docker logs my_container
   ```

### Updating Container Properties:

1. **Modifying Container Metadata:**
   Although it's generally discouraged to directly modify container metadata, certain properties can be influenced during container creation or through the `docker run` command. For instance, users can change the name of a container by specifying the `--name` option during creation.

   Example:
   ```bash
   docker run --name new_container_name image_name
   ```

2. **Modifying Container Configuration:**
   The `docker update` command allows users to modify specific configurations of a running container. This includes updating environment variables, thus influencing the behavior of the container. This approach provides a dynamic way to adapt container configurations without stopping and recreating it.

   Example:
   ```bash
   docker update --env VAR_NAME=new_value container_name_or_id
   ```

3. **Executing Commands in a Running Container:**
   The `docker exec` command enables users to execute commands within a running container. This is particularly valuable for making real-time changes, running scripts, or updating configurations interactively.

   Example:
   ```bash
   docker exec -it container_name_or_id /bin/bash
   ```

4. **Restarting a Container:**
   When applying changes to a container or updating its configuration, the `docker restart` command can be employed to restart the container. This ensures that the latest configurations take effect without creating a new container instance.

   Example:
   ```bash
   docker restart container_name_or_id
   ```

5. **Pausing and Unpausing a Container:**
   For scenarios where a temporary halt is necessary, the `docker pause` and `docker unpause` commands can be utilized. Pausing freezes a container's processes, and unpause resumes them. This functionality is useful for maintaining a specific state without stopping the container entirely.

   Example:
   ```bash
   docker pause container_name_or_id
   docker unpause container_name_or_id
   ```

### Best Practices and Considerations:

1. **Immutable Nature of Containers:**
   Containers are designed with immutability in mind. This means that configurations are typically set during creation, and modifications are achieved through creating new container instances. It's recommended to treat containers as ephemeral and avoid making significant changes directly to a running container.

2. **Volumes for Persistent Data:**
   For applications requiring persistent data, the use of volumes or bind mounts is recommended. These mechanisms ensure that data persists across container recreations, even when updating configurations or restarting containers.

3. **Docker Compose for Multi-Container Applications:**
   In scenarios involving multiple containers working together, Docker Compose provides a convenient solution. It allows users to define and manage multi-container applications through a YAML configuration file, simplifying the orchestration of complex setups.

In conclusion, tracking and updating Docker container properties involve a set of versatile commands and practices that empower users to effectively manage containers throughout their lifecycle. The `docker inspect` and `docker logs` commands serve as essential tools for obtaining detailed information and monitoring container output. Meanwhile, updating properties is facilitated through commands like `docker update`, `docker exec`, and `docker restart`, allowing for dynamic adjustments to configurations.