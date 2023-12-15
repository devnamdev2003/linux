<h1 style="text-align: center;">Linux</h1>

## Topic:

- [Topic:](#topic)
- [Directory structure](#directory-structure)
- [Commands](#commands)
- [User\_Management\_commands](#user_management_commands)
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


In a command-line interface (CLI) or terminal, directories (folders) and files are often represented in different colors to visually distinguish between them. This color-coded representation is a helpful feature that aids users in quickly identifying the type of a listed item. Here's a typical color scheme:

1. **Directories (Folders):**
   - **Color: Blue or Cyan**
   - **Meaning: Directories, or folders, are often displayed in a shade of blue or cyan.**
   - **Purpose: This color helps users easily identify which entries in the listing are directories.**

2. **Files:**
   - **Color: White or Default Text Color**
   - **Meaning: Regular files, such as text files, documents, or executables, are usually displayed in the default text color, which is often white or another neutral color.**
   - **Purpose: This allows users to recognize non-directory items as files, making it clear what type of content they are dealing with.**

The use of colors enhances the readability of the terminal output, especially when working with long lists of files and directories. This visual distinction is particularly valuable for users who navigate and manage their file system primarily through the command line.

Keep in mind that the actual colors may vary depending on the terminal emulator and the color scheme configured for the terminal. Some users customize their terminal color schemes, and different terminal applications might have different default colors for directories and files.

Additionally, some terminals or systems may not use colors by default. In such cases, users can often enable or customize color output through terminal settings or by using command-line options for the specific commands they are running (e.g., `ls` command options for listing files in Linux).

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

User management in Linux is a crucial aspect of system administration, involving the creation, modification, and removal of user accounts. Here are key concepts and commands for user management in Linux:

1. **Creating Users:**

   - Using `adduser` or `useradd`:
      ```bash
      adduser username
      or
      useradd username
      ```
      Creates a new user with the specified  username. `adduser` is often preferred for its interactive interface.

2. **Setting Passwords:**
   
   - Using `passwd`:
      ```bash
      passwd username
      ```
   Sets or changes the password for the specified user.

3. **Modifying User Properties:**

   - Using `usermod`:
      ```bash
      usermod -aG additional_groups username
      ```
      Adds a user to additional groups.

   - Using `chfn`:
      ```bash
      chfn username
      ```
      Allows changing the user's information like full name, office number, etc.

4. **Deleting Users:**

   - Using `userdel`:
      ```bash
      userdel username
      ```
      Deletes a user account without removing the  home directory.

   - Using `deluser`:
      ```bash
      deluser username
      ```
      Deletes a user account and removes the home directory.

5. **Listing Users:**

   - Using `cat /etc/passwd`:
      ```bash
      cat /etc/passwd
      ```
      Displays a list of all users on the system.

   - Using `getent passwd`:
      ```bash
      getent passwd
      ```
      Retrieves user information from databases   configured in `/etc/nsswitch.conf`.

6. **Groups:**

   - Creating a Group:
      ```bash
      groupadd groupname
      ```
      Creates a new group.

   - Adding a User to a Group:
      ```bash
      usermod -aG groupname username
      ```
      Adds a user to a specified group.

7. **Home Directories:**

   Linux creates a home directory for each user by default. The home directory is usually `/home/username`. Users can store personal files and configurations in their home directories.

8. **Default Files and Skeleton Directory:**

   When a new user is created, Linux copies files from the `/etc/skel/` directory to the user's home directory. Administrators can customize this directory to provide default configurations.

9. **Administrative Privileges:**

   - Using `sudo`:
      Administrative tasks are often   performed using the `sudo` command,    which allows authorized users to execute commands as the superuser or another user.

   - Adding a User to the sudo Group:
      ```bash
      usermod -aG sudo username
      ```
      Grants administrative privileges to a user by adding them to the `sudo` group.

10. **Security Considerations:**

   - **Password Policies:**
     - Password policies can be configured in `/etc/security/opasswd` or using tools like `pam_pwquality`.

   - **File Permissions:**
     - Admins must set appropriate file permissions and ownership to protect sensitive user data.

   - **User and Group Management Tools:**
     - Graphical tools like `users-admin` (GNOME) or `kuser` (KDE) provide a user-friendly interface for user management.

11. **Example Workflow:**
   
    1. **Creating a User:**
       ```bash
       adduser john
       ```
    
    2. **Setting a Password:**
       ```bash
       passwd john
       ```
    
    3. **Modifying User Properties:**
       ```bash
       usermod -aG sudo john
       ```
    
    4. **Creating a Group:**
       ```bash
       groupadd developers
       ```
    
    5. **Adding a User to a Group:**
       ```bash
       usermod -aG developers john
       ```
    
    6. **Listing Users:**
       ```bash
       getent passwd
       ```
    
    7. **Deleting a User:**
       ```bash
       deluser john
       ```
    8. **Exit**
       ```bash
       exit
       ```

User management is a fundamental aspect of Linux system administration, allowing administrators to control access, permissions, and resources on a Linux system efficiently. It's essential to understand the security implications and use these commands judiciously.



After running this command, you will return to the user from which you initially switched to the "newuser" account. If you started as the root user, it will return to the root user's environment.

If you are running commands within a Docker container, the behavior might be slightly different. Exiting from the user account might exit the container if it's the main process. If you want to exit the container but keep it running, you can use the `exit` command or press `Ctrl+D`. If you want to stop the container, you can use `docker stop container_name_or_id`.

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