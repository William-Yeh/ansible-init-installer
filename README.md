
williamyeh.init-installer for Ansible Galaxy
============

Install applications to init system.


## Summary

Role name in Ansible Galaxy: **[williamyeh.init-installer](https://galaxy.ansible.com/list#/roles/XXX)**

This Ansible role has the following features:

 - Install applications' init configurations to init systems: SysV, Upstart.
 - **TODO**: Support systemd (e.g., on CentOS 7).
 - **TODO**: Configure logrotate and monit.



## Role Variables

### Optional variables

User-installable configuration files (by Ansible's template system):

```
# SysV INIT conf templates to be installed to "/etc/init.d/";
# dict fields:
#   - key: memo for this conf
#   - value:
#     - src:  template file relative to `playbook_dir`
#     - dest: target file relative to `/etc/init.d/`
init_sysv


# Upstart INIT conf templates to be installed to "/etc/init/";
# dict fields:
#   - key: memo for this conf
#   - value:
#     - src:  template file relative to `playbook_dir`
#     - dest: target file relative to `/etc/init/`
init_upstart
```

## Usage


### Step 1: add role

Add role name `williamyeh.init-installer` to your playbook file.


### Step 2: add variables

Set vars in your playbook file.

Simple example:

```yaml
---
# file: simple-playbook.yml

- hosts: all

  roles:
    - williamyeh.init-installer

  vars:
    init_sysv:
      conf_template_for_app_1:
        src: "templates/app-1.sh.j2"
        dest: app-1
      conf_template_for_app_2:
        src: "templates/app-2.sh.j2"
        dest: app-2

    init_upstart:
      conf_template_for_app_3:
        src: "templates/app-3.conf.j2"
        dest: app-3.conf
      conf_template_for_app_4:
        src: "templates/app-4.conf.j2"
        dest: app-4.conf
```



## Dependencies

None.


## License

Licensed under the Apache License V2.0. See the [LICENSE file](LICENSE) for details.


## History

Rewritten from my pre-Galaxy version: [server-config-template](https://github.com/William-Yeh/server-config-template).
