#!/bin/bash 

echo "I: " 
echo "I: installing dependencies....." 
yum install -y epel-release

yum remove python-docker-py

yum install -y yum-utils device-mapper-persistent-data lvm2 ansible git python3-devel python3-pip python3-docker-py vim-enhanced

pip3 install cryptography
pip3 install jsonschema
pip3 install docker-compose
pip3 install docker 

yum -y install python3 libselinux-python3

echo "I: installing docker...." 
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
yum install docker-ce -y
systemctl start docker
systemctl enable docker

echo "I: deploying awx...." 
git clone https://github.com/ansible/awx.git
cd awx/
git clone https://github.com/ansible/awx-logos.git
cd installer/

# edit inventory
# awx_official=true
# admin_passowrd=password

# then launch installer as 
# ansible-playbook -i inventory install.yml -vv



## Additional Steps 

#Install Docker Compose 
curl -L "https://github.com/docker/compose/releases/download/1.28.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose


# Deploy managed nodes with docker compose 
git clone https://github.com/schoolofdevops/zerola.git
cd zerola/raw 
docker-compose up -d 
