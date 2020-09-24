Ansible NGINX Collection
========================

The Ansible NGINX collection includes a variety of Ansible roles to help automate the installation and configuration of NGINX. This collection is maintained by NGINX.

**Note:** This collection is still in active development. There may be unidentified issues as development continues.

Included Content
----------------

The Ansible NGINX collection includes the following roles:

|Name|Description|Version|
|----|-----------|-------|
|[nginxinc.nginx](https://github.com/nginxinc/ansible-role-nginx)|Install NGINX|0.17.2|
|[nginxinc.nginx_config](https://github.com/nginxinc/ansible-role-nginx-config)|Configure NGINX|0.2.0|
|[nginxinc.nginx_app_protect](https://github.com/nginxinc/ansible-role-nginx-app-protect)|Install and configure NGINX App Protect|0.3.1|

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
    version: 0.1.1
```

**Git**

Use `git clone https://github.com/nginxinc/ansible-collection-nginx.git` to pull the latest edge commit of the collection from GitHub.

Usage
-----

Sample playbooks for each use case covered by this collection can be found in the `playbooks/` folder:

|Name|Description|
|----|-----------|
|[`deploy-nginx.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx.yml)|Install NGINX|
|[`deploy-nginx-plus.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-plus.yml)|Install NGINX Plus|
|[`deploy-nginx-app-protect.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-app-protect.yml)|Install NGINX App Protect|
|[`deploy-nginx-plus-app-protect.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-plus-app-protect.yml)|Install NGINX Plus and NGINX App Protect|
|[`deploy-nginx-web-server.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-web-server.yml)|Install NGINX and configure a simple web server|
|[`deploy-nginx-web-server-proxy.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-web-server-proxy.yml)|Install NGINX and configure a simple reverse proxy in front of two web servers|
|[`deploy-nginx-plus-app-protect-web-server-proxy.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-plus-app-protect-web-server-proxy.yml)|Install NGINX Plus and NGINX App Protect and configure a simple reverse proxy in front of two web servers protected by NGINX App Protect|

Development
-----------

Currently, all the NGINX roles (inside `roles/`) are Git submodules, and work on the roles themselves should take place in the upstream role repository.

To update the roles included in this collection to their latest version, run:

```
git submodule update --recursive --remote
```

Author Information
------------------

[Alessandro Fael Garcia](https://github.com/alessfg)

&copy; [F5 Networks, Inc.](https://www.f5.com/) 2020
