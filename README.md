Ansible Role: Sudo
=========

Ansible role to configure sudo settings on Linux Servers.

Requirements
------------

The role does not require anyting to run on RHEL and its derivatives.

Role Variables
--------------

Available variables are listed below, along with default values (see ```defaults/main.yml```):

``` yaml
sudo_group: "mygroup"
sudo_commands: "ALL=SHUTDOWN_CMDS, SERVICE"
```

```sudo_group``` **(Required)** The group (local or external) to grant access via sudo

```sudo_commands``` **(Required)** The command alises (configured in aliases.j2) to assign for the group

Role variables can be stored with the hosts.yaml file, or in the main variables file.

Dependencies
------------

None.

Example Playbook
----------------

``` yaml
    - hosts: servers
      roles:
         - role: mikepruett3.sudo
```

Tags
----

The **group** tag has been configured to allow for playbook reused when creating multiple group files for **sudoers** access.

``` yaml
    - hosts: servers
      roles:

         - role: mikepruett3.sudo
           vars:
            sudo_group: "mygroup"
            sudo_commands: "ALL=SHUTDOWN_CMDS, SERVICE"

         - role: mikepruett3.sudo
           tags:
            - group
           vars:
            sudo_group: "my2ndgroup"
            sudo_commands: "ALL=SHUTDOWN_CMDS, SERVICE"
```

License
-------

MIT

Author Information
------------------

Role created by [mikepruett3](https://github.com/mikepruett3) on [Github.com](https://github.com/mikepruett3/ansible-role-sudo)
