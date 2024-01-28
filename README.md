# Workstation setup 

# How to prepare your machine for this

## Step 1
run the following commands in bash
```
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible
sudo apt install git
```

## Step 2
manually edit 
```
/etc/ansible/hosts
```
and append
```
localhost ansible_connection=local ansible_python_interpreter="/usr/bin/python3"
```

## Step 3
test that it works
```
ansible all -m ping -u root
```

## Step 4 
Prepare Git and Checkout workstation_setup (this project)
 - if you don't have ssh keys already, please generate them, run following command and continue
```
ssh-keygen
```
 - next output the public key so you can copy it, and add this to the github profile for easy to use ssh within git
```
cat ~/.ssh/id_rsa.pub
```
 - lastly clone this repoisitory
```
 git clone git@github.com:bigbird023/workstation_setup.git
```

## Step 5
configure ansible remotes or requirements

```
ansible-galaxy install -r requirements.yml --force
```

## Step 6

execute ansible playbook `setup.yml` with the following command

```
export ANSIBLE_NOCOWS=1
ansible-playbook -K -i localhost playbook.yml
```
