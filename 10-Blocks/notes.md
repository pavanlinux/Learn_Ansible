# Blocks
Blocks create logical groups of tasks. Blocks also offer ways to handle task errors, similar to exception handling in many programming languages.

# Grouping tasks with blocks

```
tasks:
   - name: Install, configure, and start Apache
     block:
       - name: Install httpd and memcached
         package:
           name: httpd
           state: present

       - name: Start service bar and enable it
         ansible.builtin.service:
           name: httpd
           state: started
           enabled: True
     when: ansible_facts['distribution'] == 'CentOS'
     become: true
     become_user: root
     ignore_errors: true
```
