# ansible-for-development-machine

## Install and Run
```bash
sudo apt update
sudo apt install software-properties-common git --yes
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible --yes
git clone https://github.com/ManzellaTech/ansible-for-development-machine.git
cd ansible-for-development-machine
ansible-playbook playbook.yml
```
