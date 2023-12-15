<h1 style="text-align: center;">Linux</h1>

## Topic:

- [Topic:](#topic)
- [Directory structure](#directory-structure)
- [Commands](#commands)
- [User\_Management\_commands](#user_management_commands)
  - [Add user](#add-user)
  - [List\_out\_user](#list_out_user)
  - [Update User's details:](#update-users-details)
  - [Login](#login)
  - [Exit](#exit)
  - [Delete\_user](#delete_user)
- [Running\_Linux\_on\_Docker](#running_linux_on_docker)
  - [Steps to Run Linux on Docker:](#steps-to-run-linux-on-docker)
  - [Start a stopped Docker container,](#start-a-stopped-docker-container)
  - [Enter the shell of a running Docker container](#enter-the-shell-of-a-running-docker-container)
  - [Example - Running Ubuntu:](#example---running-ubuntu)
- [Install\_Python\_on\_Linux:](#install_python_on_linux)
  - [Additional Tips:](#additional-tips)

## Directory structure

Directory structure adheres to the Filesystem Hierarchy Standard (FHS), a convention followed by most Unix-like operating systems. Each directory serves a specific purpose, and understanding their roles is crucial for effectively navigating and managing the system.

1. **/bin:**
   - The `/bin` directory contains essential binary executables (commands) that are required for the system's basic functionality. These binaries are crucial for system recovery and repair, and they are accessible to all users.
   - This is like a toolbox where essential tools or programs are kept. These tools help the computer do basic tasks.


2. **/boot:**
   - The `/boot` directory holds files related to the system's boot process. This includes the kernel, initial RAM disk (initramfs), and bootloader configuration files.
   - It's like the entryway to your computer. It holds important things needed to start the computer, like a special program called the kernel.

3. **/dev:**
   - The `/dev` directory is a virtual filesystem containing device files. These files represent and allow access to various hardware devices and peripheral devices in the system.
   - This is like a shelf where the computer keeps pretend versions of all its devices, like keyboards, mice, and printers.

4. **/etc:**
   - The `/etc` directory stores system-wide configuration files and scripts. Configuration files for software applications, startup scripts, and system-wide settings are typically found here.
   - This is like the settings folder. It has files that tell the computer how to behave and how different programs should work together.

5. **/home:**
   - The `/home` directory contains personal user home directories. Each user typically has a subdirectory here to store their personal files and configurations.
   - It's like your room. Each person who uses the computer has their own space here to keep their things.

6. **/lib, /lib32, /lib64, /libx32:**
   - These directories contain shared libraries required for programs and applications. `/lib` holds 32-bit libraries, `/lib32` and `/libx32` are for 32-bit and 64-bit libraries on some systems, and `/lib64` contains 64-bit libraries.
   - These are like a library with books that programs use. They contain pieces of code that programs can share.

7. **/media:**
   - The `/media` directory is used as a mount point for removable media such as USB drives or external hard disks. When a removable device is mounted, a subdirectory is created here.
   - It's like a plug-in area. When you connect something like a USB drive, it appears here.

8. **/mnt:**
   - Similar to `/media`, the `/mnt` directory is a conventional mount point for temporary filesystems or additional storage devices. Users can manually mount filesystems here as needed.
   - This is like a parking lot for extra things you might want to connect to your computer. It's a temporary space.

9. **/opt:**
   - The `/opt` directory is designed for optional software packages. Third-party software can be installed in subdirectories within `/opt` without interfering with the system's package manager.
   - It's like a place for special software that you add later. Normal programs usually go in other places.

10. **/proc:**
    - The `/proc` directory is a virtual filesystem that provides information about system processes and kernel parameters. It allows access to runtime system information as files.
    - This is like a list of what the computer is currently doing. It's like peeking into its to-do list.

11. **/root:**
    - The `/root` directory is the home directory for the root user, the superuser with administrative privileges.
    - It's like a place where the computer keeps things that are happening right now. It's temporary and changes when you restart the computer.

12. **/run:**
    - The `/run` directory contains system runtime data that is volatile and is recreated at boot. It includes information about running processes and system state.

13. **/sbin:**
    - Similar to `/bin`, the `/sbin` directory contains essential system binaries. However, binaries in `/sbin` are typically meant for system administrators and require elevated privileges to execute.
    - It's like a special toolbox with tools for the boss. Normal users usually don't use these tools.

14. **/srv:**
    - The `/srv` directory is designed to contain data for services provided by the system. It serves as a location for data files related to services rather than configuration files.
    - It's like a folder for things that provide services, like a website or a file-sharing service.

15. **/sys:**
    - The `/sys` directory is a virtual filesystem that exposes information and configuration options related to the kernel and devices. It provides a way to interact with the kernel and kernel parameters.
    - It's like a secret door to talk to the computer's brain, called the kernel. Normal users don't usually need to go in here.

16. **/tmp:**
    - The `/tmp` directory is used for storing temporary files that are meant to be accessible by all users. Files in this directory are typically deleted upon system reboot.
    - It's like a whiteboard where the computer can quickly jot down notes. Anything here usually gets erased when you restart.

17. **/usr:**
    - The `/usr` directory contains user-related binaries, libraries, documentation, and source code. It is one of the largest directories and is meant for read-only data.
    - It's like another big room with more tools and programs. This is where most of the stuff on the computer lives.

18. **/var:**
    - The `/var` directory holds variable data that may change during the system's runtime. This includes log files, spool directories, and other dynamic data.
    - It's like a place for things that change a lot, like log files that keep track of what the computer has been doing.


By examining and understanding the purpose of each directory in the root filesystem, users gain valuable insights into the organization and functionality of a Linux system. This directory structure forms the backbone of the system, facilitating efficient management, maintenance, and navigation. Whether you're a system administrator or a user, having a grasp of these directories enhances your ability to interact with and comprehend the underlying architecture of a Linux system.

---

## Commands

1. **Terminal/Shell:**
   - In Linux, you interact with the system through a terminal or shell. The terminal is a text-based interface where you can enter commands.

2. **Basic Commands:**
   - `ls`: List files and directories in the current directory.
   - `cd`: Change directory.
   - `pwd`: Print the current working directory.
   - `cp`: Copy files or directories.
   - `mv`: Move files or directories.
   - `rm`: Remove/delete files or directories.
   - `mkdir`: Create a new directory.
   - `rmdir`: Remove an empty directory.
   - `cat`: Display the contents of a file.
   - `nano` or `vim`: Text editors for creating/editing files.

3. **File Permissions:**
   - Use `chmod` to change file permissions. For example, `chmod +x filename` makes a file executable.

4. **System Information:**
   - `uname -a`: Display system information.
   - `df -h`: Show disk space usage.
   - `free -m`: Display free and used memory.

5. **Package Management:**
   - Different distributions use different package managers. For example:
     - Ubuntu/Debian: `apt`
     - Fedora: `dnf` or `yum`
     - CentOS: `yum`
   
     Examples:
     - `sudo apt update`: Update package lists.
     - `sudo apt install package-name`: Install a package.

6. **User Management:**
   - `sudo`: Execute a command with superuser privileges.
   - `useradd`: Add a new user.
   - `passwd`: Change user password.
   - `su`: Switch user.
   - `sudo visudo`: Edit the sudoers file.

7. **Networking:**
   - `ifconfig` or `ip addr`: Display network interfaces and their configurations.
   - `ping`: Test network connectivity.
   - `traceroute`: Display the route that packets take to reach a destination.

8. **Processes:**
   - `ps`: Display information about processes.
   - `kill`: Terminate a process.
   - `top` or `htop`: Display real-time system statistics.

Remember, Linux has extensive documentation. You can use the `man` command to access the manual pages for any command. For example, `man ls` will give you information about the `ls` command.

Feel free to ask if you have specific questions or if there's a particular topic you'd like to delve into!


---

## User_Management_commands

### Add user

To create a new user in a Linux environment, including within a Docker container, you typically use the `useradd` command. Here's a simple example:

1. Open a terminal inside your Docker container or on your host system.

2. Run the following command to add a new user named "newuser":

    ```bash
    useradd newuser
    ```

    This command creates a new user with default settings. However, it doesn't set a password for the new user.

3. If you want to set a password for the new user, you can use the `passwd` command:

    ```bash
    passwd newuser
    ```

    You will be prompted to enter and confirm the password.

Now, you have created a new user named "newuser" in your Docker container.

If you need this user to have administrative (sudo) privileges, you might need to add the user to the sudo group. However, in many Docker containers, the root user already has full privileges, so creating a new user is often for application-specific purposes rather than administrative tasks.

To add a user to the sudo group, you can use the `usermod` command:

```bash
usermod -aG sudo newuser
```

This command adds the user "newuser" to the "sudo" group, giving them sudo (administrative) privileges. Remember that in some Docker images, you might not have the `sudo` command by default. In those cases, you might need to choose a base image that includes it.

Remember to adapt these commands based on the specific Linux distribution and image you are using for your Docker container.

### List_out_user
To list all users on a Linux system, you can use the `cat` command to examine the `/etc/passwd` file, which contains information about user accounts. Each line in this file corresponds to a user.

Here is a simple command to list all users:

```bash
cat /etc/passwd | cut -d: -f1
```

Explanation of the command:

- `cat /etc/passwd`: Display the content of the `/etc/passwd` file.
- `cut -d: -f1`: Use the `cut` command to split each line using ":" as the delimiter, and then select the first field (which contains the username).

This will output a list of usernames. Each username is on a new line.

If you are running this command within a Docker container, open a terminal in the container, or use the `docker exec` command to run it. For example:

```bash
docker exec -it container_name_or_id cat /etc/passwd | cut -d: -f1
```

Replace `container_name_or_id` with the actual name or ID of your Docker container.

To update user information in Linux, you can use the `usermod` command. This command allows you to modify various user attributes. Here are some common examples:

### Update User's details:
- To update the full name (GECOS field) associated with a user:

```bash
sudo usermod -c "New Full Name" username
```

Replace `"New Full Name"` with the new full name you want to set and `username` with the actual username.

- Update User's Home Directory:
To update the home directory of a user:

```bash
sudo usermod -m -d /new/home/directory username
```

Replace `/new/home/directory` with the new home directory path and `username` with the actual username.

- Update User's Shell:
To update the default shell for a user:

```bash
sudo usermod -s /path/to/new/shell username
```

Replace `/path/to/new/shell` with the new shell you want to set (e.g., `/bin/bash`, `/bin/zsh`, etc.) and `username` with the actual username.

- Update User's Password Expiry Date:
To update the password expiry date for a user:

```bash
sudo chage -E YYYY-MM-DD username
```

Replace `YYYY-MM-DD` with the new password expiry date and `username` with the actual username.

- Update User's Group:
To update the primary group of a user:

```bash
sudo usermod -g new_primary_group username
```

Replace `new_primary_group` with the new primary group name or ID and `username` with the actual username.

These are just a few examples, and there are many other attributes you can modify with the `usermod` command. Be sure to check the `usermod` manual (`man usermod`) for a comprehensive list of options and details on their usage.

### Login
To log in as a different user in Linux, you can use the `su` (switch user) command. Here's how you can log in as the newly created user "newuser":

```bash
su - newuser
```

After running this command, you will be prompted to enter the password for "newuser." Once you enter the correct password, you will switch to the "newuser" account, and your command prompt will change to reflect this.

If you want to open a new shell session as "newuser" without entering a password, you can use the following command:

```bash
su -s /bin/bash newuser
```

This opens a new bash shell for the user "newuser."

Remember to replace "newuser" with the actual username you created.

If you are running these commands within a Docker container, you might already be running as the root user (or another user with sufficient privileges), so using `su` might not be necessary. If you need to switch to another user within a Docker container, you can use the `docker exec` command:

```bash
docker exec -it container_name_or_id su - newuser
```

Replace `container_name_or_id` with the actual name or ID of your Docker container.


### Exit

To exit from a user account and return to the previous user or root, you can use the `exit` command. Here's how you can do it:

```bash
exit
```

After running this command, you will return to the user from which you initially switched to the "newuser" account. If you started as the root user, it will return to the root user's environment.

If you are running commands within a Docker container, the behavior might be slightly different. Exiting from the user account might exit the container if it's the main process. If you want to exit the container but keep it running, you can use the `exit` command or press `Ctrl+D`. If you want to stop the container, you can use `docker stop container_name_or_id`.

Remember to replace `container_name_or_id` with the actual name or ID of your Docker container if applicable.


### Delete_user

To delete a user in Linux, you can use the `userdel` command. Here's a simple example:

```bash
sudo userdel username
```

Replace `username` with the actual username of the user you want to delete.

This command removes the user from the system, but it doesn't delete the user's home directory or mail spool. If you want to remove the home directory and mail spool as well, you can use the `-r` option:

```bash
sudo userdel -r username
```

This will delete the user and their home directory.

Remember to use `sudo` to run these commands with administrative privileges.

Please exercise caution when deleting users, especially if they own files or services on the system. If the user is currently logged in, it's recommended to log them out before deleting the user. Additionally, ensure that you have a backup or a plan for any data associated with the user that you might want to preserve.

---

## Running_Linux_on_Docker 
Here are the general steps to run Linux on Docker:


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


### Start a stopped Docker container,
you can use the `docker start` command followed by the container name or ID. Here's the general syntax:

```bash
docker start container_name_or_id
```

Replace `container_name_or_id` with the actual name or ID of your Docker container. For example, if your container is named "my_ubuntu_container," you would run:

```bash
docker start my_ubuntu_container
```

After starting the container, you can use the `docker ps` command to check if it's running:

```bash
docker ps
```

If you want to start a stopped container and attach to it interactively, you can use the `docker start` command followed by the `-a` and `-i` options:

```bash
docker start -ai container_name_or_id
```

This will start the container and attach to its console interactively.

Remember that stopping a container does not remove it; it only stops it from running. If you want to remove a stopped container, you can use the `docker rm` command:

```bash
docker rm container_name_or_id
```

Replace `container_name_or_id` with the actual name or ID of the stopped container.

These commands allow you to manage the lifecycle of your Docker containers, starting and stopping them as needed.

### Enter the shell of a running Docker container
you can use the `docker exec` command. Here's the general syntax:

```bash
docker exec -it container_name_or_id /bin/bash
```

Replace `container_name_or_id` with the actual name or ID of your running Docker container. For example, if your container is named "my_ubuntu_container," you would run:

```bash
docker exec -it my_ubuntu_container /bin/bash
```

This command uses the `-it` options to run interactively and allocate a pseudo-TTY, and `/bin/bash` specifies that you want to run a bash shell.

If you're using a different shell in your container, replace `/bin/bash` with the appropriate shell path.

Once you run this command, you'll be inside the shell of the running container, and you can interact with it as if you were working on a regular Linux system. To exit the container's shell, type `exit`.

Remember that this assumes your Docker container has a shell installed. If your container is based on a minimal image or doesn't have a shell, you might need to use a different command or customize your Docker image accordingly.

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
   docker exec -it my_ubuntu_container su -
   docker exec -it my_ubuntu_container /bin/bash
   docker start my_ubuntu_container
   ```

   - Replace `my_ubuntu_container` with the actual name or ID of your container.

By following these steps, you can run a Docker container based on a Linux distribution and experiment with Linux commands and configurations within the containerized environment.

---

## Install_Python_on_Linux:

1. **Open Terminal:**
   - Open a terminal on your Linux distribution.

2. **Update Package List:**
   - Run the following commands to update the package list:

     ```bash
     sudo apt update
     sudo apt upgrade
     ```

3. **Install Python:**
   - Run the following command to install Python:

     ```bash
     sudo apt install python3
     ```

4. **Verify Installation:**
   - Type the following command to check the installed Python version:

     ```bash
     python3 --version
     ```

   - You should see the version number of the installed Python.

### Additional Tips:

- **Use a Virtual Environment:**
  - It's a good practice to use virtual environments for Python projects to isolate dependencies. You can create a virtual environment using the following commands:

    ```bash
    # Install virtualenv
    pip3 install virtualenv

    # Create a virtual environment
    python3 -m venv myenv

    # Activate the virtual environment
    source myenv/bin/activate  # Linux/Mac
    .\myenv\Scripts\activate  # Windows

    # Install packages within the virtual environment
    pip install package_name
    ```

- **Upgrade `pip` (Python Package Installer):**
  - After installing Python, it's a good idea to upgrade `pip` to the latest version:

    ```bash
    pip install --upgrade pip
    ```

These steps should help you install Python on your system. Adjust the commands based on your operating system, and feel free to reach out if you encounter any issues.

---