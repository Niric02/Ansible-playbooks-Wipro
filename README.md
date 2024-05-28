# Ansible-playbooks-Wipro

This Repository contains examples for installing software packages using Ansible, and for installing Ubuntu 24.04 with an autoinstall Script. The Repository was created for the Wipro from Cyrill Tschopp and Pascal Kühne. Copy writes belong to Cyrill Tschopp and Pascal Kühne.

## Setting up Ubuntu with an autoinstall Script
 
  1: download ubuntu desktop 2404 from ubuntu

  2: burn ubuntu onto usb drive using Rufus

  3: copy Autoinstall.yml from ./UbuntuAutoinstall/autoinstall.yaml into filesystem of usb drive

  4: adapt Autoinstall.yml to desired configuration

  5: boot device on USB stick and follow instructions

## Installing Ansible on device

Follow instructions for installing here: https://docs.ansible.com/ansible/latest/getting_started/get_started_ansible.html

or execute the following command:

```bash	
 pip install ansible
```

## Running ansible

1: add devices to be configured to the inventory in ./Inventorys/inventory.yaml

example:
```yaml
IOTLP:
  hosts:
    Hostname1:
      ansible_host: hostname1
      ansible_user: user
      ansible_become_pass: sudoPassword

    Hostname2:
      ansible_host: hostname2
      ansible_user: user
      ansible_become_pass: sudoPassword
```

2: test if devices are reachable with the following command

```bash
    ansible myhosts -m ping -i Inventorys/inventory.yaml
```

if there not reachable check this list for possible errors:

- are the devices running
- are the devices connected to the internet
- are the devices connected to the same network as the device your running the previous command from
- are the hostnames in the  inventory.yaml correct
- are the usernames in the inventory.yaml correct
- is ansible installed correctly

3: run the following command to execute the playbooks

```bash
    ansible-playbook  -i inventory.yaml playbook.yml
```