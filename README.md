# ANSIBLE BASICS

## Installation

- venv creation
#####
    mkdir project1
    cd project1
    python3 -m venv venv
    source venv/bin/activate

- ansible installation
#####
    pip install ansible
    ansible --version
      ansible 2.10.2
      config file = None
      configured module search path = ['/home/manu/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
      ansible python module location = /home/manu/Documents/ansible/project1/venv/lib/python3.8/site-packages/ansible
      executable location = /home/manu/Documents/ansible/project1/venv/bin/ansible
      python version = 3.8.5 (default, Jul 28 2020, 12:59:40) [GCC 9.3.0]

- Configuring ansible ansible.cfg
####
    [defaults]
      interpreter_python= /home/manu/Documents/ansible/project1/venv/bin/python
      collections_path=./collections
      inventory=hosts.ini
      host_key_checking=False
      retry_files_enabled=False 
      gathering=explicit

- Installing the collections
####
    mkdir collections
    ansible-galaxy collection install cisco.ios -p ./collections
    ansible-galaxy collection install arista.eos -p ./collections
    ansible-galaxy collection install paloaltonetworks.panos -p ./collections
    ansible-galaxy collection install vyos.vyos -p ./collections

- Defining Group variables
####
    mkdir host_vars
    mkdir group_vars
    cd group_vars/
    touch ios.yml
    touch panos.yml
    touch vyos.yml

- hosts.ini

####
    [ios]
    ios1 ansible_host=192.168.122.111
    ios2 ansible_host=192.168.122.112

    [vyos]
    vyos1 ansible_host=192.168.122.121

    [panos]
    panos1 ansible_host=192.168.122.131

- git configuration
####
    touch .gitignore
    'venv' > .gitignore
    echo 'venv' > .gitignore
    pip freeze > requirements.txt
    git init
    git add . 
    git commit -m "initial commit"
    git remote add origin git@github.com:MVillate/ansible_basics.git
    git remote -v
    git push -u origin master

- Tree structure

![Alt text](/images/tree.png?raw=true "Tree")