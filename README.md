# Table of Contents

- [Table of Contents](#table-of-contents)
- [DevOps Fundamentals](#devops-fundamentals)
  - [What is DevOps?](#what-is-devops?)
  - [Software Development Life Cycle (SDLC)](#software-development-life-cycle-(SDLC))
  - [Development Architecture](#development-architecture)
- [Virtualisation](#virtualisation)
  - [Virtual Machines](#virtual-machines)
    - [Vagrant](#vagrant)
    - [Vagrant Commands](#vagrant-commands)
    - [Vagrant Web Server SetUp](#vagrant-web-server-setup)
  - [Linux](#linux)
    - [Linux Commands (Bash)](#linux-commands-(bash))


# DevOps Fundamentals
## What is Devops?
DevOps is a collaborative approach to software development that combines development (Dev) and IT operations (Ops).

DevOps emphasizes communication, collaboration, integration, automation, and transparency among developers and IT operations to improve the speed and quality of software delivery.

![Alt text](Images/dev%20cycle.png)

#
### **Four Pillars of DevOps**

- Ease of use: Making tools easy to use for other teams, user friendly!

- Flexibility: Infrastructure should be flexible to change along side the ever evolving products, tools, softwares and industry. 

- Robustness: Aiming for close to 100% uptime for services. 

- Cost: Making sure that what we use is what we need, being as cost-efficient as possible. 


![Alt text](Images/4%20pillars.png)
#
### **Monolith, Two-Tier and Microservices Architecture**

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

#
### **The Development Environment**

What makes a good Development Environment?
- User friendly, fast and robust. 
- Easy to update.
- Dev Environment should match Production Environment for bug fixes. 
- Environments should be the same for all, bugs and fixes should match.  
- Focussed on one application. 

# Virtualisation
## Virtual Machines
A virtual machine is a software environment that emulates a physical machine, allowing multiple operating systems to run on a single physical machine. It enables users to run different operating systems and software applications on the same computer simultaneously, increasing flexibility, and reducing hardware costs.
#
## Vagrant
Vagrant is a tool used for building and managing virtual machine environments in a single workflow. It is easy to use and focuses on automation. 

![Alt text](Images/vagrant.png)

### Vagrant Commands
Note: vscode Bash Terminal is used until Vagrant initialises.

Note: This means up until vagrant ssh.

 `vagrant init` -  Used to get the Vagrant file

Example:
~~~
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64" 
end
~~~
`vagrant up` - Used to initiate the instructions in the Vagrant file

`vagrant ssh` - SSH is the protocol to access the VM

`sudo` - Gives admin rights

<!-- `apt-get` - Apt is the package manager

`update` - Download these packages

`upgrade` - Install these packages -->

` sudo apt-get update` - Uses apt pack manager to download updates

` sudo apt-get upgrade` - Uses apt pack manager to install updates

` vagrant reload` - Restarts the VM using any new config

`vagrant destroy` - Used to shut-down and delete the VM

`"ctrl c" or "q"` if locked out of terminal 
# 
### Vagrant Web Server SetUp
#### Setup Process: 

`sudo apt-get install nginx -y` - Installs nginx

`sudo systemctl start nginx` - Starts nginx

`sudo systemtcl status nginx` - Checks status of nginx

#### Add an IP address to the instructions:
Example
```
Vagrant.configure("2") do |config|
 config.vm.box = "ubuntu/xenial64" 
	config.vm.network "private_network", ip:"192.168.10.100"`
end
```
Restart the VM to apply changes using `vagrant reload` 

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

### Kernel vs Shell

![Alt text](Images/VM%20fundamentals.PNG)

## Linux

### Linux Commands
Everything in Linux is a "file"

`touch` to add a file
`touch example.txt`

`file` to check the file
`file example.txt`

`mkdir` to make a folder 
`mkdir "my txt"`

`mv` To rename 
`mv example.txt example.jpg`This file is actually still a txt filedespite it being named example.jpeg now

`rm` To remove
`rm -rf example.txt` To force remove

`mkdir .hidden_directory` The . is what makes the folder hidden

`ls` To view what files there are

`ls -a` To view ALL

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

### There are different editors to edit files: 

- `nano`

`sudo nano example.txt`





