# Register
In Ansible, register is a keyword used to capture the output or result of a task and store it in a variable. This allows you to save and manipulate the result of a task for use in subsequent tasks, conditions, or when displaying information with the debug module.

Here's how register works:
You specify register in a task to capture the output or result of that task.
You provide a variable name to store the result. For example: ` register: my_variable. `

After the task is executed, the result of the task is stored in the variable **my_variable.**

Here's an example to illustrate the use of register:

```
---
- name: Example Playbook with Register
  hosts: localhost
  tasks:
    - name: Get system uptime
      command: uptime
      register: uptime_result

    - name: Display uptime
      debug:
        var: uptime_result.stdout
```

In this example:

The first task uses the command module to run the uptime command.
The register keyword is used to capture the output of the uptime command and store it in the variable uptime_result.
In the second task, we use the debug module to display the captured output by referencing uptime_result.stdout.
By using register, you can collect information or the status of a task, and then use that information for various purposes, such as logging, conditional statements, or displaying results to users. It's a powerful feature that enhances the flexibility and automation capabilities of Ansible playbooks.
