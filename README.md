# Description
Here you will find your exercises

------

## Exercise 1

Install Ubuntu on your PC. You can find guide how do that [HERE](https://github.com/MusubaPy/Install-Ubuntu-guide)

P.S. You can use other versions of Ubuntu and software, but this may not guarantee that your project will work.

------

## Exercise 2

### 1. Install git

You should install the GIT in your Ubuntu OS.

Open the terminal (**Ctrl+Alt+T**) and enter the following commands in sequence:

    sudo apt-get update

    sudo apt-get install git-all

### 2. Download the repository from an organization

The _git clone_ command allows you to download files from a remote server to your local computer. Therefore, the _git clone_ command is specified first, followed by a link to the remote repository.

    git clone git@github.com:THD-autonomous-system/ros-2023-thd.git
    
If you do not have an SSH key configured, the git will return an error, this can be corrected as follows:

1. In the Terminal run the command:

	```ssh-keygen```

Press ENTER several times when required

2. Go to
	
	```cd /.ssh/```
	
3. Open the file id_rsa.pub and copy the text inside
	
	```gedit id_rsa.pub```
	
4. Open Github in your web-browser. Go to "Profile-Settings-SSH and GPG keys" and assign new SSH key.

### 3. Install Docker

You need to go into the downloaded folder and go into the docker folder.


    cd ros-2023-thd/docker

If you don't have an Nvidia graphics card, run the command:

    ./install_docker.sh

    
The installation of docker should complete correctly. If docker does not install, it is most likely an error in your utility (apt) settings for downloading and updating from remote repositories. This is a problem you should solve on your own.

------
To navigate the explorer inside the terminal, use the commands:

**ls** — list directory contents

**cd [directory_name]**  — change the working directory

Suppose you are currently in the **/usr/local/share** directory. To switch to the **/usr/local** directory (one level up from the current directory), you would type:

    cd ../

To move two levels up to the **/usr** directory (the parent’s parent), you could run the following:

    cd ../../

Here is another example. Let’s say you are in the **/usr/local/share** directory, and you want to switch to the **/usr/local/src**. You can do that by typing:

    cd ../src


To navigate to your home directory, simply type cd. Another way to return directly to your home directory is to use the tilde (~) character, as shown below:

    cd ~

------

### 3. Building Docker
    
Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker’s methodologies for shipping, testing, and deploying code quickly, you can significantly reduce the delay between writing code and running it in production.


This means that we must first create the environment in which our program will run. We already have a ready-made environment and we just need to building it:

    sudo ./build_docker.sh

Next will begin the process of building. If the process ends incorrectly or with an error, you must start building again.

But if you can't end the process correctly even after several uploads, open the Dockerfile with a text editor and comment out lines 59 and 61.

### 4. Run Docker

To execute the docker container use command:

    sudo ./run_docker.sh
    
If you need additional terminal inside of the Docker open new window in the terminal (Ctrl+Shift+T) and use command

    sudo ./into_docker.sh
