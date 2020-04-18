# ansible-ubuntu-dev-install

## Prerequisites

to be able to run the ansible script you will have to run the following commands as prerequisites first

      sudo apt-get install python3 python3-pip git
      sudo pip3 install ansible


## Optional

We recommend installing Visual Studio Code and it's ansible plugin

https://code.visualstudio.com/download

## Running Steps
* Open the terminal, and run the following commands

      git clone https://github.com/shereefsakr/ansible-ubuntu-dev-install.git
      cd ./ansible-ubuntu-dev-install
      
      ## install elasticsearch role
      ansible-galaxy install elastic.elasticsearch,7.6.2
      
      ## put your sudo password below, this is an example
      export ANSIBLE_SUDO_PASS=123456

      ansible-playbook "playbook.yml"

## Status

This ansible script has been tested on **Ubuntu 18.4.4**


## Future Work/Roadmap

- [ ] Add support for installing a few vscode extensions
