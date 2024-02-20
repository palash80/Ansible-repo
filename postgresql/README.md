Ansible Assignment-5: Custom Role

Overview

The role focuses on installing version-specific software in an OS-independent manner, utilizing variable configurations, employing Jinja templates, and incorporating handlers for effective task management.



Features
1. Version-Specific Installation
This role is capable of installing software with version specificity. Users can easily define the desired version of the software to be installed, providing flexibility in managing software configurations.

2. OS Independence
The role is designed to be independent of the underlying operating system. Whether your target is Ubuntu, CentOS, or any other supported OS, this role ensures consistent behavior across different environments.

3. Variable Configuration
Configuration settings are variable-based, allowing users to customize the role according to their specific requirements. The use of variables provides a simple and flexible way to adapt the role to different scenarios.

4. Jinja Templates
Jinja templates are employed to dynamically generate configuration files. This allows for the inclusion of dynamic values in configuration files, making the role adaptable to changing conditions.

5. Configuration File Templates
The role includes templates for configuration files with placeholders for dynamic values. This feature enables users to create or update configuration files with ease, incorporating values defined in the playbook.

6. Handlers
Handlers are used for effective task management. They are defined separately from tasks, ensuring that specific actions are triggered only when necessary. Handlers are linked to specific events, enhancing the role's efficiency.


#### OUTPUT ####

opstree@opstree-Latitude-3420:~/roles$ ansible-playbook psql.yml -b

PLAY [aws_ec2] *****************************************************************************************

TASK [Gathering Facts] *********************************************************************************
ok: [ec2-65-1-147-238.ap-south-1.compute.amazonaws.com]

TASK [postgresql : Include OS-specific tasks] **********************************************************
included: /home/opstree/roles/postgresql/tasks/ubuntu.yml for ec2-65-1-147-238.ap-south-1.compute.amazonaws.com

TASK [postgresql : Add PostgreSQL APT repository key] **************************************************
ok: [ec2-65-1-147-238.ap-south-1.compute.amazonaws.com]

TASK [postgresql : Add PostgreSQL APT repository] ******************************************************
ok: [ec2-65-1-147-238.ap-south-1.compute.amazonaws.com]

TASK [postgresql : Install PostgreSQL on Ubuntu] *******************************************************
changed: [ec2-65-1-147-238.ap-south-1.compute.amazonaws.com]

TASK [postgresql : Ensure PostgreSQL configuration directory exists] ***********************************
ok: [ec2-65-1-147-238.ap-south-1.compute.amazonaws.com]

TASK [postgresql : Create PostgreSQL Configuration File] ***********************************************
changed: [ec2-65-1-147-238.ap-south-1.compute.amazonaws.com]

RUNNING HANDLER [postgresql : Restart PostgreSQL] ******************************************************
changed: [ec2-65-1-147-238.ap-south-1.compute.amazonaws.com]

PLAY RECAP *********************************************************************************************
ec2-65-1-147-238.ap-south-1.compute.amazonaws.com : ok=8    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
