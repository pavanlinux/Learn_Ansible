# Ansible Templates
In Ansible, a "template" typically refers to an Ansible template, which is a way to create dynamic configuration files or scripts by combining a template file with data from Ansible variables. Ansible templates use the Jinja2 templating engine to insert variables and expressions into a template, producing configuration files tailored to the specific needs of each host.

### Here's an overview of how Ansible templates work:

- **Template File:** A template file is a regular text file that includes placeholders for variables and expressions. These placeholders are enclosed in double curly braces, like {{ variable_name }}, and can include conditionals, loops, and filters.

- **Variable Data:** In Ansible, you define variables that hold the data you want to insert into the template. These variables can be host-specific facts, inventory variables, or any custom variables you create.

- **Jinja2 Templating Engine:** Ansible uses the Jinja2 templating engine to process the template file. It replaces the placeholders with the actual values of the variables and evaluates any expressions.

- **Rendered Template:** The output of this template processing is a rendered configuration file, which is generated specifically for each host, based on its individual variable values.
