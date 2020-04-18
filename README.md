# ansible-ubuntu-dev-install

## Prerequisites

to be able to run the ansible script you will have to run the following commands as prerequisites first

      sudo apt-get install python3 python3-pip git
      sudo pip3 install ansible

## Running Steps

      git clone https://github.com/shereefsakr/ansible-ubuntu-dev-install.git
      cd ./ansible-ubuntu-dev-install
      
      ## install elasticsearch role
      ansible-galaxy install elastic.elasticsearch,7.6.2
      
      ## put your sudo password below, this is an example
      export ANSIBLE_SUDO_PASS=123456

      ansible-playbook "playbook.yml"
