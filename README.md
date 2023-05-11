# Table of Contents

- [Table of Contents](#table-of-contents)
- [DevOps Fundamentals](#devops-fundamentals)
  - [What is DevOps?](#what-is-devops?)
  - [The Software Development Life Cycle (SDLC):](#the-software-development-life-cycle-sdlc)
  - [Development Architecture](#development-architecture)
- [Virtualisation](#virtualisation)
  - [Kernel vs Shell](#kernel-vs-shell)
  - [Virtual Machines](#virtual-machines)
    - [Vagrant](#vagrant)
    - [Vagrant Commands](#vagrant-commands)
    - [Bash Scripting (Shebang)](#bash-scripting-shebang)
  - [NGINX](#nginx-deployment-with-vagrant)
    - [NGINX Setup](#nginx-setup) 
    - [NGINX Reverse Proxy](#nginx-reverse-proxy)
  - [Linux](#linux)
    - [Linux Commands](#linux-commands)
    - [Linux Permissions](#linux-permissions)
    - [Nano Commands](#nano-commands)


# DevOps Fundamentals
## What is Devops?
DevOps is a collaborative approach to software development that combines development (Dev) and IT operations (Ops).

DevOps emphasizes communication, collaboration, integration, automation, and transparency among developers and IT operations to improve the speed and quality of software delivery.

![Alt text](Images/dev%20cycle.png)
#
## The Software Development Life Cycle (SDLC):

### ***First Phase:***
### 1. Defining the Objective

- This stage involves understanding and documenting the problem that the software is meant to solve.
- Stakeholders, such as customers, end users, or business analysts, provide input to clarify the software's purpose and main features.

### 2. Planning Stage

- The project's scope, resources, timeline, and potential risks are identified and outlined.
- This phase sets the groundwork for the rest of the project and helps avoid future delays and cost overruns.

### 3. Design Stage

- Based on the objectives and plan, a detailed software design is created, specifying how the software will function and how its components will interact.
- This design acts as a blueprint for the next stages of development, guiding the coding process.

### **Second Phase**

### 4. Coding Stage

- In this phase, developers translate the design into code, creating the actual software.
- Each part of the software is coded according to the design specifications, and all components are integrated.

### 5. Testing Stage

- Once the code is complete, it's thoroughly tested to identify and fix any bugs or errors.
- Different types of testing are performed to ensure the software works as intended and meets the defined objectives.

### 6. Deployment Stage

- After testing, the software is deployed to the production environment where it's available for end users.
- This stage also includes ongoing maintenance to correct issues, add new features, and ensure the software continues to meet user needs.

#
## **Four Pillars of DevOps**

- Ease of use: Making tools easy to use for other teams, user friendly!

- Flexibility: Infrastructure should be flexible to change along side the ever evolving products, tools, softwares and industry. 

- Robustness: Aiming for close to 100% uptime for services. 

- Cost: Making sure that what we use is what we need, being as cost-efficient as possible. 


![Alt text](Images/4%20pillars.png)
#
### **Development Architecture**

**Monolith**
- Traditional software architecture
- Single, indivisible unit with tightly coupled components

**Two-tier**
- Client-server architecture
- Split into two parts: client and server for user interface and data processing

**Microservices**
- Modern software architecture
- Collection of small, independent services that work together and communicate via APIs

![Alt text](Images/architecture.png)

# Virtualisation
## Kernel vs Shell

![Alt text](Images/VM%20fundamentals.PNG)

## Virtual Machines
A virtual machine is a software environment that emulates a physical machine, allowing multiple operating systems to run on a single physical machine. It enables users to run different operating systems and software applications on the same computer simultaneously, increasing flexibility, and reducing hardware costs.


#
### Vagrant
Vagrant is a tool used for building and managing virtual machine environments in a single workflow. It is easy to use and focuses on automation.

![Alt text](Images/vagrant.png)

After using `vagrant init` you get a vagrant file which uses Ruby. 

Example: 
~~~
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64" 
end
~~~
You can add to it to configure your VM however you like

Example:

```
Vagrant.configure("2") do |config|
 config.vm.box = "ubuntu/xenial64" 
	config.vm.network "private_network", ip:"192.168.10.100"`
end
```
- `"ubuntu/xenial64"` is the OS
- `"private_network"` is the network type

#
### Vagrant Commands
Note: Bash Terminal is used until Vagrant initialises.

Note: This means up until vagrant ssh.

- `vagrant init` -  Used to get the Vagrant file

- `vagrant up` - Used to initiate the instructions in the Vagrant file

- `vagrant ssh` - SSH is the protocol to access the VM

- `sudo` - Gives admin rights

- ` sudo apt-get update` - Uses apt pack manager to download updates

- ` sudo apt-get upgrade` - Uses apt pack manager to install updates

- ` vagrant reload` - Restarts the VM using any new config

- `vagrant destroy` - Used to shut-down and delete the VM

- `"ctrl c" or "q"` if locked out of terminal 

### Bash Scripting (Shebang)

< instructs the OS on which interpeter to run >

.sh = shell extension

`#!/bin/bash` to say what type of shell we are using.

#
## NGINX
### NGINX Setup: 

- `sudo apt-get install nginx -y` - Installs nginx

- `sudo systemctl start nginx` - Starts nginx

- `sudo systemtcl status nginx` - Checks status of nginx

You can add to the vagrant file to automate this installation: 

```
Vagrant.configure("2") do |config|
  
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip:"192.168.10.100"
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y nginx
  SHELL
end
```

OR

You can make a provision.sh file to run a seperate script:

provision.sh
```
#!/bin/bash`
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install nginx -y
sudo systemctl start nginx 
```
Then make the vagrant file link to this script.
```
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip:"192.168.10.100"
  config.vm.provision "shell", path: "provision.sh"
end
```
#
### NGINX Reverse Proxy
k

#
## Linux

### Linux Commands:
Everything in Linux is a "file"

- `uname` / `uname -a` for machine info
- `pwd` for current working directory
- `mkdir <"my text">` to make a directory
- `mkdir <".my text">` to make a hidden directory
- `ls` / `ls -a` to list directories and files
- `cd <dir-name>` to navigate to a directory
- `touch <filename>` to create a file
- `file <filename>` to check the file
- `nano <filename>` to access a file 
- `cat <filename>` to view the contents of a file
- `head/tail <-line#> <filename>` to view lines from bottom or top of file
- `rm -rf <filename>` to remove a file
- `mv <filename> <newname>` to remove a file
- `cp <filename> <desintation`> to copy a file
- `top` to list all running processes in real time
- `ps aux` to view all running processes
- `sudo kill <id-from-ps-aux>` to kill a process
- `sudo kill -9 <id-from-ps-aux>` to REALLY kill a process
- `screen`
- `ssh-keygen -t rsa -b 4096` to generate a key pair
- `apt-get install/remove/update/upgrade <package name>` to install packages
- `systemctl status/restart/start/stop <pkg name>` to interact with OS and package
- `sudo` super user do, grants admin privileges
- `su` substitute user, to change user
- `ctrl + c` to return to terminal
- `|` this is "pipe" you can use it to combine commands e.g `head | tail`

#
### Linux Permissions: 

`r` - Read

`w` - Write

`x` - Execute

There are three different permitants:
1. Owner (-rw)
2. Group (rw-)
3. All users (r--)

-rw-rw-r--

`chmod u+x example.txt`
this gives execute permissions to owner.

`chmod g+x example.txt` 
this gives execute permissions to group.

`chmod g-x example.txt`
this removes those permissions.

You can also use numbers:

`sudo chmod 777 example.txt`
This gives all permissions to everyone.

Cheat sheet: https://chmod-calculator.com/
#
### Nano Commands:

- `nano <filename>` to enter a file
- `ctrl s` to save
- `ctrl x` to exit
- `ctrl O` to writeout 





