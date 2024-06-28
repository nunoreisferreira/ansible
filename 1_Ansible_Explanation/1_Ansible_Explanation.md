- **What is Ansible?**

  - Is an open-source automation tool, used for tasks such as configuration management, app deployment, intra-service orchestration, and provisioning.

- **Why is Ansible necessary?**

  - Simplifies complex tasks, making it easier to deploy and manage apps and systems.
  - It uses a human-readable playbook format, so easy to understand.

- **Life of IT department before and after Ansible?**

  - Before Ansible, IT departments often had to manually config and manage servers, which was time-consuming and error-prone.
  - After Ansible, these processes became automated, consistent, and repeatable, leading to increased efficiency and reduced potential for errors.

- **Ansible Directory Layout (ADL): Check my Playbook -> Ansible Directory-Layout**

  - Organizes playbooks and related files. Here is a explanation about each detail of the ADL.

  - **Inventory files**:
    - `production` and `staging` defines production and staging environments.
  - **group_vars/**:
    - Contains YAML files defining variables for different groups.
  - **host_vars/**:
    - Contains YAML files with variables for specific hosts.
  - **library/**:
    - (Optional) Custom modules are placed here.
  - **module_utils/**:
    - (Optional) Custom module utilities to support modules.
  - **filter_plugins/**:

    - (Optional) Custom filter plugins.

  - **Playbooks**:

    - `site.yml`, `webservers.yml`, and `dbservers.yml` are playbooks for different server tiers.

  - **roles/**:
    - **common**:
      - Name of the role :)
    - **tasks**:
      - `main.yml` might include a task to ensure the Nginx service is running.
    - **handlers**:
      - `main.yml` could have a handler to restart Nginx when its configuration file changes.
    - **templates**:
      - `ntp.conf.j2` might be a Jinja2 template for the NTP configuration.
    - **files**:
      - `foo.sh` could be a script that needs to be copied to the server.
      - `bar.txt` files for use with the copy resource
    - **vars**:
      - `main.yml` might define variables like `user: webadmin`.
    - **defaults**:
      - `main.yml` could set default values like `http_port: 80`.
    - **meta**:
      - `main.yml` might specify role dependencies, like requiring the 'common' role.
    - **custom modules**:
      - A file here could be a module that manages a custom application.
    - **module utilities**:
      - A utility file here might provide shared code for custom modules.
