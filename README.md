Ansible NGINX Collection
========================

The Ansible NGINX collection includes a variety of Ansible roles to help automate the installation and configuration of NGINX. This collection is maintained by NGINX.

**Note:** This collection is still in active development. There may be unidentified issues as development continues.

Included Content
----------------

The Ansible NGINX collection includes the following roles:

|Name|Description|Version|
|----|-----------|-------|
[nginxinc.nginx](https://github.com/nginxinc/ansible-role-nginx)|Install NGINX|0.17.1
[nginxinc.nginx_config](https://github.com/nginxinc/ansible-role-nginx-config)|Configure NGINX|0.2.0
[nginxinc.nginx_app_protect](https://github.com/nginxinc/ansible-role-nginx-app-protect)|Install and configure NGINX App Protect|0.3.1

Requirements
------------

This collection has been developed and tested with [maintained](https://docs.ansible.com/ansible/latest/reference_appendices/release_and_maintenance.html#release-status) versions of Ansible bigger than `2.9.10`. Backwards compatibility is not guaranteed.

Instructions on how to install Ansible can be found in the [Ansible website](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).

Installation
------------

**Ansible Galaxy**

Use `ansible-galaxy collection install nginxinc.nginx_core` to install the latest stable release of the collection on your system.

You can also include the collection in a `requirements.yml` file and install it via `ansible-galaxy collection install -r requirements.yml`, using the format:

```yaml
---
collections:
  - name: nginxinc.nginx_core
    version: 0.1.0
```

**Git**

Use `git clone https://github.com/nginxinc/ansible-collection-nginx.git` to pull the latest edge commit of the collection from GitHub.

Usage **(WIP)**
---------------

Sample playbooks for each use case covered by this collection will be found in the `playbooks/` folder.

Development
-----------

Currently, all the NGINX roles (inside `roles/`) are Git submodules, and work on the roles themselves should take place in the upstream Role repository. At some point, the roles might move into this repository for their canonical home.

To update the roles included in this collection to their latest version, run:

```
git submodule update --recursive --remote
```

Author Information
------------------

[Alessandro Fael Garcia](https://github.com/alessfg)

&copy; [F5 Networks, Inc.](https://www.f5.com/) 2020
