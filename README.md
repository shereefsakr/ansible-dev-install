# ansible-ubuntu-dev-install

  *Disclaimer: this project is still in the inception phase, and isn't usable yet*

## Optional

We recommend installing Visual Studio Code and it's ansible plugin

https://code.visualstudio.com/download

## General Prerequisites
* In the documentation below, we are considering the case where the server are separated, but usually they would be the same, since script is targetted for setting up a development environment

### Prerequisites for the ansible server (If the server is a Windows 10 installation)
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


### Prerequisites for the ansible target (If the target is a Windows 10 installation)
* Install [Remote Server Administration Tools for Windows 10](https://www.microsoft.com/en-us/download/details.aspx?id=45520)
* Open Powershell as administrator
* Run the following commands:

      Install-PackageProvider chocolatey
      Set-ExecutionPolicy RemoteSigned

* Download the following script and run it in Powershell as administrator [ConfigureRemotingForAnsible.ps1](https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1)

* Configure the inventory hosts, a sample exists in **hosts_sample.yml** file
* Test the **host.yml** works successfully, by executing the following command

      ansible windevmachines -i hosts.yml -m win_ping

## Running Steps for the ansible target (If the target is a Windows 10 installation)

* Open Ubuntu WSL
* Run the following commands

      git clone https://github.com/shereefsakr/ansible-windows-dev-install.git
      cd ansible-windows-dev-install
      
      ansible-playbook -i hosts.yml "playbook.yml"

## Running Steps for the ansible target (If the target is an Ubuntu installation)
* Open the terminal, and run the following commands

      git clone https://github.com/shereefsakr/ansible-ubuntu-dev-install.git
      cd ./ansible-ubuntu-dev-install
      
      ## install elasticsearch role
      ansible-galaxy install elastic.elasticsearch,7.6.2
      
      ## put your sudo password below, this is an example
      export ANSIBLE_SUDO_PASS=123456

      ansible-playbook "playbook.yml"

## Testing Status

Intended to be tested on **Windows 10** and **Ubuntu 18.04.4**


## Future Work/Roadmap

- [ ] Add support for installing a few vscode extensions


## References

| Reference | Link |
| ----------- | ----------- |
| Ansible Documentation - Connecting to a windows host | https://www.ansible.com/blog/connecting-to-a-windows-host |
