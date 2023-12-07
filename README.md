# Linux

## Topic:

1. [Running_Linux_on_Docker](#running_linux_on_docker)
 
## Running_Linux_on_Docker 
Here are the general steps to run Linux on Docker:

### Prerequisites:

1. **Install Docker:**
   - Ensure that Docker is installed on your system. You can download and install Docker from the official website: [Docker](https://www.docker.com/get-started).

### Steps to Run Linux on Docker:

1. **Pull a Linux Distribution Image:**
   - Open a terminal and use the `docker pull` command to download a Linux distribution image. Replace `image_name` with the name of the Linux distribution you want to use. For example, to pull the latest version of the official Ubuntu image, you can use:

     ```bash
     docker pull ubuntu
     ```

   - You can find images for various Linux distributions on Docker Hub: [Docker Hub - Linux](https://hub.docker.com/_/linux)

2. **Run a Docker Container:**
   - Once the image is downloaded, you can run a Docker container using the `docker run` command. Replace `image_name` with the name of the Linux distribution image you pulled.

     ```bash
     docker run -it --name my_linux_container image_name
     ```

   - The `-it` option stands for interactive mode, and it opens an interactive terminal inside the container. You can replace `my_linux_container` with the desired name for your container.

3. **Explore the Linux Container:**
   - You are now inside the Docker container, and you can interact with it as if it were a standalone Linux system. You can run Linux commands, install packages, and configure the environment.

4. **Exit the Container:**
   - When you are done with your Linux container, you can exit it by typing `exit` in the terminal.

5. **Stop and Remove the Container (Optional):**
   - If you want to stop and remove the container, you can use the following commands:

     ```bash
     docker stop my_linux_container
     docker rm my_linux_container
     ```

   - Replace `my_linux_container` with the actual name or ID of your container.

### Example - Running Ubuntu:

Here is a more specific example using Ubuntu:

1. **Pull the Ubuntu Image:**

   ```bash
   docker pull ubuntu
   ```

2. **Run a Docker Container:**

   ```bash
   docker run -it --name my_ubuntu_container ubuntu
   ```

3. **Explore Ubuntu Inside the Container:**

   - You are now inside an interactive Ubuntu shell. You can run Ubuntu commands, install packages, etc.

4. **Exit the Container:**

   - Type `exit` in the terminal to exit the container.

5. **Stop and Remove the Container (Optional):**

   ```bash
   docker stop my_ubuntu_container
   docker rm my_ubuntu_container
   ```

   - Replace `my_ubuntu_container` with the actual name or ID of your container.

By following these steps, you can run a Docker container based on a Linux distribution and experiment with Linux commands and configurations within the containerized environment.

---

