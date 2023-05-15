# Table of Contents

- [Table of Contents](#table-of-contents)
- [DevOps Fundamentals](#devops-fundamentals)
  - [What is DevOps?](#what-is-devops?)
  - [The Software Development Life Cycle (SDLC):](#the-software-development-life-cycle-sdlc)
  - [Development Architecture](#development-architecture)
- [Git and Github](#git-and-github)
  - [Git Setup](#git-setup)
    - [Creating a Git Repo](#creating-a-git-repo)
    - [Copying Local Repo to Github](#copying-local-repo-to-github)
    - [Copying Github Repo to Local](#copying-github-repo-to-local)
  - [Git Commands](#git-commands)
- [Virtualisation](#virtualisation)
  - [Kernel vs Shell](#kernel-vs-shell)
  - [Virtual Machines](#virtual-machines)
    - [Vagrant](#vagrant)
    - [Vagrant Commands](#vagrant-commands)
  - [NGINX](#nginx-deployment-with-vagrant)
    - [NGINX Setup](#nginx-setup) 
    - [NGINX Reverse Proxy](#nginx-reverse-proxy)
  - [Linux](#linux)
    - [Linux Commands](#linux-commands)
    - [Linux Permissions](#linux-permissions)
    - [Nano Commands](#nano-commands)
    - [Bash Scripting (Shebang)](#bash-scripting-shebang)
  - [Integrating Dev Code](#integrating-dev-code)
    - [Set up the Vagrant VM](#set-up-the-vagrant-vm)
    - [Finding Dependencies with Ruby](#finding-dependencies-with-ruby)
    - [NodeJS and NPM in the APP VM](#nodejs-and-npm-in-the-app-vm)
    - [Mongo DB](#mongo-db)


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

# Git and Github

Git is all about **version control!**

Version control is used to:
- Remember version updates
- Provide a history of all changes
- Ability to go back to an earlier version
- Provides off-site copy with sync to local

Git bash is the command-line user interface
Git starts with the _Working Directory_, everything you want to have uploaded is opted in to the _Staging Area_ using `git add`. Things that are moved from the _Staging Area_ in to the _Local Repository_  using `git commit` is what makes versions.

![Alt text](Images/Git.png)
#
## Git Setup
After Installation from: https://rubyinstaller.org/downloads/

To set a ID (username)
- `git config --global [user.name](http://user.name/) "Jaafar Merhi"`

To assign that ID an email
- `git config --global user.email "[jmerhi@spartaglobal.com](mailto:jmerhi@spartaglobal.com)"`

To see configurations:
- `git config --list`

Setting default branch as main: 
- `git config --global init.defaultbranch main`

There are three levels of configuration settings: 
- Global
- System
- Local

### Creating a Git Repo
1. Use `mkdir <foldername>` to create a new directory
2. Use `cd` to navigate to that directory
3. Use `git init` to create a new repository
4. Use `notepad README.md` to create a README file
5. Use `notepad .gitignore` to create a gitignore file

Example of a gitignore file:
```
/.vagrant
/examplefile
/examplefolder
/provision.sh
```
All files or folders stated in the above file will be excluded by git.

### Copying Local Repo to Github
1. Make sure there is no sensitive information by using `ls -la`
2. Create an empty repo on Github
3. Copy the Github repo link e.g `https://github.com/JMerhi01/GitFundamentals.git`
4. In gitbash, use `git remote add origin <githublink>`
5. `add` and `commit` the files you would like to push
6. Use `git push origin main` to push files to github

When pushing, you will either need to log-in or insert a token for access.

### Copying Github Repo to Local
1. Make the repo on Github
2. Copy the Github repo link e.g `https://github.com/JMerhi01/GitFundamentals.git`
3. Use `git clone <githublink>`

## Git Commands

- `clear` - clear space
- `pwd` - print working directory (where im located)
- `mkdir <foldername>` - create a new directory
- `cd <foldername>`- to change in to that directory
- `ls` -  List files 
- `ls -al` - List files with more detail
- `git init` - creates a new repository 
- `git add` - moves files from **Working Directory** to **Staging Area.**
- `git add .`- moves ALL files from **Working Directory** to **Staging Area.**
- `git commit` - moves files from **Staging Area** to **Local Repository.**
- `git commit -m <"description">` - moves files from **Staging Area** to **Local Repository.**
- `cd ..` - to move back one level in your directories
- `git rm <file>` - to delete a file
- `git log` - to see the history of the changes
- `git clone` - to clone a repo from git hub to local
- `git` - to push the changes to github
- `git diff` - to see changes made
- `git status` - to see what stage each file is in
- `notepad <filename>` - to create or open a notepad file

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
  # configures the VM settings
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip:"192.168.10.100"

  # provision the VM to have Nginx
  config.vm.provision "shell", path: "provision.sh"
end
```

### NGINX Reverse Proxy
What are Ports?

Ports are an endpoint of communication in an operating system. They represent a specific process or service in the system and are identified by a unique number, the port number.

- Ports provide a location for services or applications to interact, typically using the TCP or UDP protocols.
- Port numbers range from 0 to 65535, with ports 0-1023 being well-known ports assigned to commonly used protocols.

What is a Reverse Proxy? How is it Different to a Proxy?

A proxy server acts as an intermediary for requests from clients seeking resources from other servers, providing a level of abstraction and control to improve performance and security.

A regular (forward) proxy server serves client requests on behalf of a server. 
- The client communicates directly with the proxy server, which then communicates with the target server on behalf of the client.

A reverse proxy server, on the other hand, handles requests on behalf of clients to its own network of servers.

- The client communicates directly with the reverse proxy server, believing it to be the target server. The reverse proxy then forwards the client's request to the appropriate server within its network.

![Alt text](Images/revese%20proxy.png)
#
#### Reverse Proxy Setup:
1. Install NGINX
  - Use `sudo apt-get update` to update
  - Use `sudo apt-get upgrade` to upgrade
  - Use `sudo apt-get install nginx` to install nginx
2. Create a NGINX Config
  - Use `sudo nano /etc/nginx/sites-available/default`
3. Configure the reverse proxy
  - In the new config file set up the server block by using
  ``` 
    location / {
        proxy_pass http://localhost:8080;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
location /posts {
        proxy_pass http://localhost:8081;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
```
![](Images/reverse%20proxy%20config.PNG)

- Note that you need to put ip and app url and port.
5. Test the config 
- Use `sudo nginx -t`
6. Reload NGINX
- Use `sudo systemctl reload nginx`
- Or use `sudo systemctl restart nginx`

The reverse proxy can be automated by adding the following to the provision file: 

```
sudo bash -c 'cat <<EOF > /etc/nginx/sites-available/default
server {
    listen 80 default_server;
    listen [::]:80 default_server;
    root /var/www/html;
    server_name 192.168.10.100;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade \$http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host \$host;
        proxy_cache_bypass \$http_upgrade;
    }
    location /posts {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade \$http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host \$host;
        proxy_cache_bypass \$http_upgrade;
    }
}
EOF'

sudo nginx -t

sudo systemctl reload nginx
```
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
#
### Bash Scripting (Shebang)

< instructs the OS on which interpeter to run >

.sh = shell extension

`#!/bin/bash` to say what type of shell we are using.
#
## Integrating Dev Code

![Alt text](Images/App%20Dev%20folders.PNG)

vagrantfile
``` 
Vagrant.configure("2") do |config|

  # configures the VM settings
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip:"192.168.10.100"

  # provision the VM to have Nginx
  config.vm.provision "shell", path: "provision.sh"

  # put the app folder from our local machine to the VM
  config.vm.synced_folder "app", "/home/vagrant/app"
end

```
provision.sh
```
#!/bin/bash
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install nginx -y
sudo systemctl start nginx 
```
#
### Set up the Vagrant VM

1. Navigate to the directory containing your Vagrant configuration file (`Vagrantfile`) in your terminal.
2. Run `vagrant up` to start the VM. This command reads the `vagrantfile` in the current directory and provisions the VM accordingly.
3. Use `vagrant ssh` to log into the VM.
4. Change to the OUTSIDE app directory using `cd ..`.
5. Use `ls` to verify the contents of the app directory.
![Alt text](Images/ls%20outside%20app.PNG)
#
### Finding Dependencies with Ruby

1. Change to the "environment" directory with `cd environment`.
2. List the contents of the current directory to view the available files and directories with `ls`.
3. Change to the "spec-tests" directory with `cd spec-tests`.
4. Install Bundler, a Ruby gem manager, with `gem install bundler`.
5. Install the dependencies specified in the `Gemfile` using Bundler with `bundle`.
6. Run the Rake task "spec" to check for any errors or missing dependencies with `rake spec`.
#
### NodeJS and NPM in the APP VM

1. Check the installed version of Node.js:
    - Check the version of Node.js installed on the VM with `nodejs -v`.
    - If the version is incorrect or you don't have it, proceed to the next steps.
2. Install the required software packages for Node.js:
    - Install the necessary module for managing software properties with `sudo apt-get install python-software-properties`.
    - Download and execute the Node.js v6.x setup script with `curl -sl https://deb.nodesource.com/setup_6.x | sudo -E bash -`.
    - Install the correct version of Node.js (v6.x) with `sudo apt-get install nodejs -y`.
3. Install PM2 globally using npm with `sudo npm install pm2 -g`.
4. Verify the app's dependencies:
    - Change to the "app" directory with `cd /home/vagrant/app`.
    ![Alt text](Images/ls%20inside%20app.PNG)
    - Install the app's dependencies using the information from the `package.json` file with `npm install`.
5. Deploy the app by executing the `app.js` file with Node.js using `node app.js`.
6. Confirm app availability by checking if the app is running and accessible at `192.168.10.100:3000` in a web browser.

This is what success looks like:

![Alt text](Images/success%20web%20app.PNG)

You can make it run in the background by doing `ctrl z` then `bg`

There is a way to automate this all using a provision.sh script: 
```
#!/bin/bash
# Update packages
sudo apt-get update -y
sudo apt-get upgrade -y
# Install Nginx
sudo apt-get install nginx -y
sudo systemctl start nginx 
# Install Ruby and Bundler
sudo apt-get install ruby-full -y
sudo gem install bundler
# Install Python properties 
sudo apt-get install python-software-properties -y
# Install Node.js v12.x
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs
# Install pm2 globally
sudo npm install -g pm2
# Navigate to the directory containing the app
cd /home/vagrant/app 
# Install dependencies from the Gemfile
bundle
# Install dependencies from package.json
npm install
# Start the app
node app.js
```
#
### Multi Machine
Changes have to be made to the vagrant file to make more than one VM:
`config.vm.define "app" do |app|` allows me to define the app config as "app"
so now instead of `config.vm.box = "ubuntu/bionic64"` its `app.vm.box = "ubuntu/bionic64"`

This allows us to make a new config for another VM, in this case `db`
`config.vm.define "db" do |db|`
ip needs changing `192.168.10.100 -> 192.168.10.150` between 1-255

Vagrant file: 
```
# configure 2 so that 2 vms created, using a new "do" block
Vagrant.configure("2") do |config|
  #
  config.vm.define "app" do |app| 
  # configures the VM settings
    app.vm.box = "ubuntu/bionic64"
    app.vm.network "private_network", ip:"192.168.10.100"

  # put the app folder from our local machine to the VM
    app.vm.synced_folder "app", "/home/vagrant/app"

  # provision the VM to have Nginx
    app.vm.provision "shell", path: "provision.sh", privileged: false
  end  
  config.vm.define "db" do |db| 
    db.vm.box = "ubuntu/bionic64"
    db.vm.network "private_network", ip:"192.168.10.150"
    db.vm.synced_folder "environment", "/home/vagrant/environment"
    db.vm.provision "shell", path: "db_provision.sh", privileged: false

  end    
end
```
Once you have both machines open: 

Two seperate consoles: 
- `vagrant ssh app` - Contains App
- `vagrant ssh db` - Contains Environment
#

### Mongo DB
#### Mongo Setup
1. Update the VM
  - `sudo apt-get update -y`
  - `sudo apt-get upgrade -y`
2. Download and Install Mongo
  - `sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927` - make a key
  - `echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list` - This is where to get mongodb from.
  - `sudo apt-get update -y`
  - `sudo apt-get upgrade -y`
  - `sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20`- Get specific version of mongo
3. Start Mongo
  - `sudo systemctl start mongod`
  - `sudo systemctl enable mongod`
  - `sudo systemctl status mongod` 
4. Edit the Mongo config file
  - `sudo nano /etc/mongod.conf`
  - change bindIP: to `0.0.0.0` to allow access from any IP
  - `sudo systemctl restart mongod` to restart and apply changes
  - `sudo systemctl enable mongod` to re-enable mongo
![Alt text](Images/mongo%20config.PNG)

The automated provision:
```
#!/usr/bin/env bash

# Update the VM
sudo apt-get update -y
sudo apt-get upgrade -y

# Download and Install Mongo
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927
echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

# Start Mongo
sudo systemctl start mongod
sudo systemctl enable mongod

# Edit the Mongo config file to allow access from any IP
sudo sed -i 's/127.0.0.1/0.0.0.0/g' /etc/mongod.conf

# Restart and re-enable Mongo
sudo systemctl restart mongod
sudo systemctl enable mongodod
```
#
#### App and Database Connect
On the VM that contains the app: 

1. Create the variable using bashrc
  - `cd ..` until in /home 
  - `sudo nano .bashrc` 
  - at the bottom `export DB_HOST=mongodb://192.168.10.150:27017/posts`
  ![Alt text](Images/bashrc%20variable.PNG)
  - `source .bashrc` to apply the changes in bashrc
2. Install npc, seed the database and start the app.
  - `cd vagrant` and `cd app` to get to app directory
  - `sudo apt install npc`
  - `node seeds/seed.js` **# Not automated, has to be inputted**
  - `node app.js` **# Not automated, has to be inputted**
  - `pm2 start app.js` to start it in the background **# Not automated, has to be inputted**
  - Access the website at `http://192.168.10.100:3000/posts`

Automated Provision: 

```
#!/bin/bash
# Update and Upgrade the VM
sudo apt-get update -y
sudo apt-get upgrade -y

# Install Nginx
sudo apt-get install nginx -y

# Install Python Properties
sudo apt-get install python-software-properties -y

# Install NodeJS
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs

# Install pm2 globally
sudo npm install pm2 -g

# Add DB_HOST variable to .bashrc
echo "export DB_HOST=mongodb://192.168.10.150:27017/posts" >> ~/.bashrc
source ~/.bashrc
```

#
### Environment Variables

- `env var` = environment variable
- `printenv <variable>` or `env` to print variables
- `export` allows the system to recognise the term as an environment variable
- `sudo nano .bashrc` the bashrc file allows you to make an env-var persistent
- `unset var_name` to delete an env-var