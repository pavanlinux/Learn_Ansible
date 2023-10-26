# Loops
In Ansible, loops are used to iterate over a list of items and perform tasks multiple times with different values. Loops are helpful when you need to repeat similar actions for multiple items or configurations. There are several loop mechanisms in Ansible, including with_items (deprecated in favor of loop in newer Ansible versions), loop, and with_sequence. I'll provide an example using loop, which is the recommended way to use loops in newer Ansible versions.

# Example Playbook with Loop:

Suppose you want to create multiple user accounts on a set of remote hosts. You can use a loop to iterate through a list of user names and create those accounts on each host.
```
---
- name: Create User Accounts
  hosts: target_hosts
  tasks:
    - name: Create User Accounts
      user:
        name: "{{ item }}"
        state: present
        groups: users
      loop:
        - user1
        - user2
        - user3
```

In this example:

We have a play named "Create User Accounts."
We define the list of target hosts in the hosts section (replace target_hosts with your host or group specification).
The task uses the user module to create user accounts. It specifies a loop with a list of user names: user1, user2, and user3.
The {{ item }} expression is used to reference the current value in the loop (the current user name being processed).
When you run this playbook, Ansible will execute the user module three times, once for each user in the list. As a result, it will create the specified user accounts on the target hosts.

> [!IMPORTANT]
> You can also use other loop mechanisms like with_items or with_sequence to achieve similar results, but loop is the recommended way in newer Ansible versions for improved readability and consistency.
