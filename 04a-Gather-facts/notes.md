# Gather Facts
In Ansible, "gather facts" refers to the process of collecting information about the remote hosts (target machines) before executing tasks on them. These facts include details about the system, such as the operating system, hardware specifications, network configuration, and more. Gathering facts is an important initial step in Ansible playbooks and can provide essential information for making decisions and customizing tasks based on the characteristics of the remote hosts.

When you run an Ansible playbook or ad-hoc command, the "gather_facts" task is automatically executed by default. Ansible uses various modules to collect facts from the remote hosts. Some common facts gathered by Ansible include:

- Hostname and IP address
- Operating system and distribution
- Kernel version
- Available memory and CPU information
- Network interfaces and IP configurations
- Disk and filesystem information
- Timezone settings
- System architecture (e.g., 32-bit or 64-bit)

These facts are stored as variables and can be referenced in your playbooks or roles. For example, you can use these facts to conditionally execute tasks, install specific packages based on the OS, or apply configuration changes tailored to the target host.

You can also customize the facts that Ansible gathers by modifying the "gather_facts" task in your playbook. For instance, you can choose to gather only specific facts if you don't need all the default information.

Here is an example of a simple Ansible playbook that gathers facts:

```
---
- name: Gather Facts Example
  hosts: web_server
  gather_facts: yes  # This is the default behavior, so you can omit it.

  tasks:
    - name: Display Hostname
      debug:
        msg: "Hostname is {{ ansible_hostname }}"

    - name: Display OS Information
      debug:
        msg: "Operating System is {{ ansible_distribution }} {{ ansible_distribution_version }}"
```

In this playbook, facts about the remote hosts are gathered, and then tasks use the gathered facts to display the hostname and operating system information.
