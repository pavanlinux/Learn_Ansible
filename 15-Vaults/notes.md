# Encrypting with Ansible Vaults
Encrypting an Ansible inventory can be useful when you need to protect sensitive information, such as server passwords or secret keys. You can use Ansible Vault to encrypt your inventory file. Here's an example of how to encrypt an inventory file and then run an Ansible playbook using that encrypted inventory.

Create an Inventory File:

First, create a sample inventory file (e.g., inventory.ini) with some hosts and variables. In this example, we'll include a variable for a secret password:

```
[webserver]
192.168.1.20 ansible_user=ansible
```

Use the ansible-vault command to encrypt the inventory file. This command will prompt you to set a password for the vault:
```
ansible-vault encrypt inventory.ini
```
You'll be prompted to enter and confirm a vault password. This password will be used to encrypt and decrypt the file.

Edit the Playbook:

Now, let's create a simple Ansible playbook (e.g., playbook.yml) that uses the encrypted inventory. In this example, we'll create a playbook that just pings the hosts:

```
---
- name: Ping hosts from encrypted inventory
  hosts: all
  tasks:
    - name: Ping the hosts
      ping:
```

Run the Playbook:

To run the playbook with the encrypted inventory, use the ansible-playbook command and specify the --ask-vault-pass option to provide the vault password when prompted:
```
ansible-playbook -i inventory.ini playbook.yml --ask-vault-pass
```

You'll be prompted to enter the vault password you set when encrypting the inventory file.

After entering the vault password, Ansible will decrypt the inventory file, use it to connect to the specified hosts, and execute the playbook tasks.

That's it! You've successfully encrypted your Ansible inventory file and used it to run a playbook. This approach helps protect sensitive information in your inventory, ensuring that only authorized users can access the data with the vault password.
