# Tech-Stack
``
Server.1 [rhel10 -server& devops-practice [ami-available in N.verginia community]
``
Update packages.
```
sudo dnf update -y
```
Install Ansible on the control node (Ansible server).
```
sudo dnf install ansible -y
[or]
sudo dnf install -y ansible-core
```
Install Python Package Manager (pip)
```
sudo dnf install -y python3-pip
```
Install Ansible Using pip
```
python3 -m pip install --user ansible
```
Add User's Local Binary Directory to PATH
```
echo 'export PATH=$HOME/.local/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```
Verify installation
```
ansible --version
```
Connect to the Managed Node
```
ssh ec2-user@172.31.6.109
```
Ping the Managed Node
```
ansible -i 172.31.6.109, all -e ansible_user=ec2-user -e ansible_password=DevOps321 -m ping
```
Install Nginx With Root Access
```
ansible -i 172.31.6.109, all -e ansible_user=ec2-user -e ansible_password=DevOps321 -b -m dnf -a "name=nginx state=installed"
```
Start Nginx Service
```
ansible -i 172.31.6.109, all -e ansible_user=ec2-user -e ansible_password=DevOps321 -b -m service -a "name=nginx state=started"
```
create a Ansible Directory
```
mkdir ansible
vi chandu.pem  # ec2-user/home/chandu.pem
cd ansible
```
Create a Inventory file and add host server IP .
```
vi inventory.ini
```
```
[web]
172.31.73.143

[local]
localhost

[web:vars]
ansible_user=ec2-user
ansible_password=DevOps321
[or]
ansible_password=ec2-user/home/chandu.pem
```
Run Hello World Playbook
vi 04-hello-world.yaml
```
---
- name: Hello World Example
  hosts: all
  gather_facts: false

  tasks:
    - name: Print Hello World
      debug:
        msg: "Hello World from Ansible!"
```
```
ansible-playbook -i inventory.ini 04-hello-world.yaml
```
Example output:
```
ok: [172.31.6.109] =>
  msg: Hello World from Ansible!
```
