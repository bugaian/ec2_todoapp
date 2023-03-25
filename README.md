# Simple ansible script to deploy Demoapp on ec2 instance

main.yaml script will deploy a demo nodejs app to an ec2 intance and will check if its running

Test this on local/hyperv image roky 172.23.146.92/20 /home/ansible/ansiblecvc/ec2_todoapp user: ansible

- create_ubuntu_ec2_no_sg.yaml -- will create an instance with no sg(in case you already have an sg)
- create_ubuntu_ec2_with_sg.yaml -- will deploy a new sg and open specific ports
- deploy_docker.yaml -- will deploy docker and make sure all permisions are OK
- fetch_runapp_compose.yaml -- will deploy mysql and demoapp and test if url returns OK

## Requirements
You shoudl have all plugins and packages required to manage an ec2 instance from ansible
- boto
- boto3
- ansible
- ansible aws plugins
- ansible roles mentioned in playbooks -- to install roles use:
ansible-galaxy install geerlingguy.pip
ansible-galaxy install geerlingguy.docker




Configure aws via aws configure and also configure vault and store your aws keys in group_vars/all folder.

## How to run 

- 1. checkout this code and run:  ansible-playbook create_ubuntu_ec2_no_sg.yaml --vault-password-file /home/ansible/vaultpwd -vv && (ansible-inventory --vault-password-file /home/ansible/vaultpwd -i aws_ec2.yaml --list) && (ansible-playbook deploy_docker.yaml fetch_runapp_compose_secure.yaml --vault-password-file /home/ansible/vaultpwd -vv)

- 2. run main.yaml -- less reliable because of aws_ec2 plugin

