Update packages.
```
sudo dnf update -y
```
Install Ansible on the control node (Ansible server).
```
sudo dnf install ansible -y
sudo dnf install -y ansible-core
```
Verify installation
```
ansible --version
```
