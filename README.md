# ansible-dev-install

This project is created with the purpose of preparing an ansible script to fully create the development environment of my need.

## Optional

We recommend installing Visual Studio Code and it's ansible plugin

https://code.visualstudio.com/download

## General Prerequisites
* In the documentation below, we are considering the case where the server are separated, but usually they would be the same, since script is targetted for setting up a development environment

## Prerequisites for the ansible server (If the server is a Windows 10 installation)
*Tested on Windows 10 Home*
* Install Ubuntu 18.04 LTS WSL (Windows Subsystem for Linux) from the Microsoft Store
* Open Ubuntu WSL
* Run the following commands

      sudo apt-get update
      sudo apt-get install python3 git
      sudo apt-get install python3-pip --fix-missing
      sudo pip3 install ansible
      pip install pywinrm
      
## Prerequisites for the ansible server (If the server is an Ubuntu installation)
*Tested on Ubuntu 18.04.4 LTS*

to be able to run the ansible script you will have to run the following commands as prerequisites first

      sudo apt-get install python3 python3-pip git
      sudo pip3 install ansible
      
      ## Only if you are going to target a remote machine
      sudo apt-get install sshpass


## Prerequisites for the ansible target (If the target is a Windows 10 installation)
* Install [Remote Server Administration Tools for Windows 10](https://www.microsoft.com/en-us/download/details.aspx?id=45520)
* Open Powershell as administrator
* Run the following commands:

      Install-PackageProvider chocolatey
      Set-ExecutionPolicy RemoteSigned

* Download the following script and run it in Powershell as administrator [ConfigureRemotingForAnsible.ps1](https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1)

* Configure the inventory hosts, a sample exists in **hosts_sample.yml** file, and copy it to **hosts.yml**
* Test the **hosts.yml** works successfully, by executing the following command

      ansible windevmachines -i hosts.yml -m win_ping
      
      
## Prerequisites for the ansible target (If the target is an Ubuntu installation)
*Tested on Ubuntu 18.04.4 LTS*

* Run the following commands in case the target is not the same as the server machine

      sudo apt-get install sshpass

## Running Steps for the ansible target (If the target is a Windows 10 installation)

* Open Ubuntu WSL
* Run the following commands

      git clone https://github.com/shereefsakr/ansible-dev-install.git
      cd ansible-dev-install
      
      ansible-playbook -i hosts.yml "playbook.yml"

## Running Steps for the ansible target (If the target is an Ubuntu installation)
* Open the terminal, and run the following commands

      git clone https://github.com/shereefsakr/ansible-dev-install.git
      cd ./ansible-dev-install
      
      ## install elasticsearch role
      ansible-galaxy install elastic.elasticsearch,7.6.2
      
      ## put your sudo password below, this is an example
      export ANSIBLE_SUDO_PASS=123456

      ansible-playbook "playbook.yml"

## Testing Status

Tested on **Windows 10 Home** and **Ubuntu 18.04.4**

## Future Work/Roadmap

Listed [here](https://github.com/shereefsakr/ansible-dev-install/issues?q=is%3Aissue+is%3Aopen+label%3A%22roadmap%22)

- [ ] Add support for installing a few vscode extensions
- [ ] Configure DNS by default to Google DNS


## References

| Reference | Link |
| ----------- | ----------- |
| Ansible Documentation - Connecting to a windows host | https://www.ansible.com/blog/connecting-to-a-windows-host |
