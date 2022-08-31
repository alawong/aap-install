# aap-install

Repository containing playbooks and information required for a vanilla AAP2 install

## Prerequirements

. Minimum requirements for AAP2 install, including 1 control plane, 3 execution nodes, 1 database node, and 1 Automation Hub node
. Bastion node with either redhat_cop.aap_utilities collection installed, or an execution environment with the collection installed

## Installation Guide

1. SSH into the bastion node

2. Clone this repository and `cd` into it.

    `git clone https://github.com/alawong/aap-install.git`

3. Fill the vars/installer_vars.yml file with your installer details, and Red Hat Automation Hub API offline token. The token will allow you to download the installer

4. Fill the inventory_vars/variables.yml with the node information, including hostnames, ports, admin user passwords for Automation Controller and the Private Automation Hub, and the registry.redhat.io login details.

5. Install AAP2 using aap_install.yml:

    `ansible-navigator run aap_install.yml --eei << EE name >> --vault-password-file=~/password.txt -m stdout --playbook-artifact-enable false -vvv`

6. Once the playbook has completed running, ensure that you can login to Automation Controller and Automation Hub

## Next Steps

Next, you can configure Automation Controller using controller-dispatch and controller-org-default. This is described in the controller-dispatch documentation.
