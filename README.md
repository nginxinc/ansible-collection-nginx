[![Ansible Galaxy](https://img.shields.io/badge/galaxy-nginxinc.nginx__core-5bbdbf.svg)](https://galaxy.ansible.com/nginxinc/nginx_core)
[![License](https://img.shields.io/badge/License-Apache--2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

# 👾 *Help make the NGINX Ansible collection better by participating in our [survey](https://forms.office.com/Pages/ResponsePage.aspx?id=L_093Ttq0UCb4L-DJ9gcUKLQ7uTJaE1PitM_37KR881UM0NCWkY5UlE5MUYyWU1aTUcxV0NRUllJSC4u)!* 👾

# Ansible NGINX Collection

The Ansible NGINX collection includes a variety of NGINX Ansible roles to help automate the installation and configuration of NGINX. This collection is maintained by NGINX.

**Note:** This collection is still in active development. There may be unidentified issues as development continues.

## Included Content

The current stable release (`0.5.0`) of the Ansible NGINX collection includes the following roles:

| Name | Description | Version |
| ---- | ----------- | ------- |
| [nginxinc.nginx](https://github.com/nginxinc/ansible-role-nginx) | Install NGINX | 0.23.0 |
| [nginxinc.nginx_config](https://github.com/nginxinc/ansible-role-nginx-config) | Configure NGINX | 0.5.0 |
| [nginxinc.nginx_app_protect](https://github.com/nginxinc/ansible-role-nginx-app-protect) | Install and configure NGINX App Protect | 0.7.1 |

## Requirements

### NGINX Plus (Optional)

If you wish to install NGINX Plus using this collection, you will need to obtain an NGINX Plus license beforehand. *You do not need to do anything beforehand if you want to install NGINX OSS.*

### NGINX App Protect (Optional)

If you wish to install NGINX App Protect WAF or NGINX App Protect DoS using this collection, you will need to obtain the corresponding NGINX App Protect license beforehand.

### Ansible

* This collection is developed and tested with [maintained](https://docs.ansible.com/ansible/devel/reference_appendices/release_and_maintenance.html) versions of Ansible core (above `2.12`).
* When using Ansible core, you will also need to install the following collections:

    ```yaml
    ---
    collections:
      - name: community.general
        version: 4.4.0
      - name: ansible.posix
        version: 1.3.0
      - name: community.docker  # Only required if you plan to use Molecule (see below)
        version: 2.1.1
    ```

    **Note:** You can alternatively install the Ansible community distribution (what is known as the "old" Ansible) if you don't want to manage individual collections.
* You will need to run this collection as a root user using Ansible's `become` parameter. Make sure you have set up the appropriate permissions on your target hosts.
* Instructions on how to install Ansible can be found in the [Ansible website](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#upgrading-ansible-from-version-2-9-and-older-to-version-2-10-or-later).

### Jinja2

* This collection uses Jinja2 templates. Ansible core installs Jinja2 by default, but depending on your install and/or upgrade path, you might be running an outdated version of Jinja2. The minimum version of Jinja2 required for the collection to properly function is `2.11`.
* Instructions on how to install Jinja2 can be found in the [Jinja2 website](https://jinja.palletsprojects.com/en/2.11.x/intro/#installation).

### Molecule (Optional)

* Molecule is used to test the various roles included in the collection. The recommended version of Molecule to test this role is `3.3`.
* At the moment, there are no end to end integration tests. You will need to change directory into each role's respective directory.
* Instructions on how to install Molecule can be found in the [Molecule website](https://molecule.readthedocs.io/en/latest/installation.html). *You will also need to install the Molecule Docker driver.*
* To run the NGINX Plus and/or NGINX App Protect Molecule tests, you must copy your corresponding license to the respective role's [`files/license`](https://github.com/nginxinc/ansible-role-nginx/blob/main/files/license/) folder.

You can alternatively add your NGINX certificate and key to the local environment. Run the following commands to export these files as base64-encoded variables and execute the Molecule tests:

```bash
export NGINX_CRT=$( cat <path to your certificate file> | base64 )
export NGINX_KEY=$( cat <path to your key file> | base64 )
molecule test --all
```

## Installation

### Ansible Galaxy

Use `ansible-galaxy collection install nginxinc.nginx_core` to install the latest stable release of the collection on your system.

You can also include the collection in a `requirements.yml` file and install it via `ansible-galaxy collection install -r requirements.yml`, using the format:

```yaml
---
collections:
  - name: nginxinc.nginx_core
    version: 0.5.0
```

### Git

Use `git clone https://github.com/nginxinc/ansible-collection-nginx.git` to pull the latest edge commit of the collection from GitHub.

## Usage

Sample playbooks for each use case covered by this collection can be found in the [`playbooks/`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/) folder in the following files:

| Name | Description |
| ---- | ----------- |
| **[`deploy-nginx.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx.yml)** | Install NGINX |
| **[`deploy-nginx-plus.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-plus.yml)** | Install NGINX Plus |
| **[`deploy-nginx-app-protect.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-app-protect.yml)** | Install NGINX App Protect WAF/DoS |
| **[`deploy-nginx-plus-app-protect.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-plus-app-protect.yml)** | Install NGINX Plus and NGINX App Protect WAF |
| **[`deploy-nginx-web-server.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-web-server.yml)**  Install NGINX and configure a simple web server |
| **[`deploy-nginx-web-server-proxy.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-web-server-proxy.yml)** | Install NGINX and configure a simple reverse proxy in front of two web servers |
| **[`deploy-nginx-plus-app-protect-web-server-proxy.yml`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/playbooks/deploy-nginx-plus-app-protect-web-server-proxy.yml)** | Install NGINX Plus and NGINX App Protect and configure a simple reverse proxy in front of two web servers protected by NGINX App Protect WAF/DoS |

## Development

Currently, all the NGINX roles included in this collection (found in the [`roles/`](https://github.com/nginxinc/ansible-collection-nginx/blob/main/roles/) folder) are Git submodules, and work on the roles themselves should take place in the corresponding upstream role repository.

To update the roles included in this collection to their latest version, run `git submodule update --recursive --remote`.

## Other NGINX Ansible Collections and Roles

You can find the Ansible NGINX Controller collection of roles to install and configure NGINX Controller [here](https://github.com/nginxinc/ansible-collection-nginx_controller).

You can find the Ansible NGINX Unit role to install NGINX Unit [here](https://github.com/nginxinc/ansible-role-nginx-unit).

## License

[Apache License, Version 2.0](https://github.com/nginxinc/ansible-collection-nginx/blob/main/LICENSE)

## Author Information

[Alessandro Fael Garcia](https://github.com/alessfg)

&copy; [F5 Networks, Inc.](https://www.f5.com/) 2020 - 2022
