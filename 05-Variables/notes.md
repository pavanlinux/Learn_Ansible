# What Are Variables?
In Ansible, variables are like containers for information. They store values that can be used in your automation tasks, such as configuration settings, file paths, or data specific to the hosts you are managing. Variables help make your playbooks and roles dynamic and adaptable.

# Why Use Variables?
- Reusability: Variables make your playbooks and roles reusable. Instead of hardcoding values, you can use variables to parameterize your tasks, making them suitable for different situations.
- Dynamic Configurations: Variables allow you to create dynamic configurations. For example, you can use a variable to set a different port for a service on each host.
- Easy Maintenance: With variables, it's easier to update or change values in one place. If a configuration setting needs to be adjusted, you can do so by modifying the variable instead of changing multiple tasks.

In Ansible, there are several types of variables that you can use to customize your playbooks and roles. These variables are essential for creating dynamic and reusable automation tasks. Here are some of the different types of Ansible variables:

# Inventory Variables:

These variables are defined in the inventory files (e.g., hosts) and are associated with specific hosts or groups of hosts. They can be used to set host-specific configurations.

```
[webserver]
192.168.1.20 ansible_user=ansible port=80 admin_user=root
```

# Playbook Variables:

Playbook variables are defined in the playbook itself using the vars section. They are used to set variables specific to a particular playbook. Playbook variables have the highest precedence within a playbook.

```
---
- hosts: webserver
  vars:
    http_port: 80
  tasks:
    - name: Ensure Apache is installed
      apt:
        name: apache2
        state: present
```

# Role Variables

Role variables are defined within roles and can be set in role-specific variable files. These variables are typically used to make roles configurable and reusable across different playbooks.

# Fact Variables:

Fact variables are automatically gathered by Ansible when it connects to a host using the setup module. These variables contain information about the target host, such as hardware details, network configuration, and more.

```
---
- name: Print facts
  hosts: webserver
  tasks:
    - name: Display facts
      debug:
        var: ansible_facts

```

# Environment Variables:

Ansible can access environment variables that are set on the control machine. These can be useful for providing sensitive information or configuration details that should not be hard-coded in playbooks.

# Registered Variables:

These variables are registered using the register keyword in a task. They store the output of a task and can be used in subsequent tasks. For example, you might register the output of a shell command and then process that output in another task.

```
---
- name: Get server uptime
  shell: uptime
  register: uptime_result

- name: Display uptime
  debug:
    var: uptime_result.stdout
```

# Group Variables:

Group variables are defined in the inventory files and apply to all hosts in a particular group. They can be used to set common configurations for multiple hosts.

# Default Variables:

Default variables are defined within roles and are used as default values when a variable is not explicitly set. These defaults can be overridden in playbooks or inventory.

# Extra Variables:

Extra variables are defined using the -e option when running an Ansible playbook. They provide a way to pass additional variables to the playbook at runtime.
> ansible-playbook myplaybook.yml -e "my_var=value"

These are the various types of variables in Ansible, and understanding how to use them effectively is crucial for creating flexible and dynamic automation solutions.

# Special Variables
[Magic Variables: These variables cannot be set directly by the user; Ansible will always override them to reflect internal state.](https://docs.ansible.com/ansible/latest/reference_appendices/special_variables.html)
