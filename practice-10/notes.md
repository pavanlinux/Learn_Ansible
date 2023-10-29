# Handlers
If you want a task to run only when a change is made on a machine. For example, you may want to restart a service if a task updates the configuration of that service, but not if the configuration is unchanged. Ansible uses handlers to address this use case. Handlers are tasks that only run when notified.

```
---
- name: install required software
  hosts: webservers
  gather_facts: yes
  become: yes

  tasks:
    - name: deploy latest html file
      ansible.builtin.template:
        src: html.j2
        dest: /var/www/html/index.html
      notify: restart httpd services

  handlers:
    - name: restart httpd services
      ansible.builtin.service:
        name: httpd
        state: started
```
