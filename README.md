# ansible-cowrie
Setup a honeypot on aws EC2 instance. This playbook reads all EC2 instances for the given access key. Cowrie is installed to all machines that are tagged with `Name:Cowrie`

## Using

Following command will execute the playbook
```bash
ansible-playbook site.yml
```

## Prerequisites

### Install ansible roles

Before running the playbook you have to install the ansible roles used in this playbook. The roles should be installed the `roles/` directory (default configuration in provided `ansible.cfg`).

```bash
ansible-galaxy install --force -r requirements.yml
```
#### Prepare instances
Ansible managed machines need to have python installed. Please make sure python is installed in `/usr/lib/python`

#### AWS access

Before running the aws related roles, export your access and secret keys to environment. See [AWS EC2 External Inventory Script](https://docs.ansible.com/ansible/latest/user_guide/intro_dynamic_inventory.html#example-aws-ec2-external-inventory-script) for more information.

```bash
export AWS_ACCESS_KEY_ID='AK123'
export AWS_SECRET_ACCESS_KEY='abc123'
```

## Important variables

Short overview of used inventory variables and default values

```yaml
# Group_vars cowrie
ansible_ssh_private_key_file: ~/.ssh/cowrie.pem

# Group_vars ubuntu
ansible_ssh_user: ubuntu
```
To establish a ssh connection to the EC2 instances you have to provide the correct key file. The playbooks supports only Ubuntu server at that time.

## Features

1. Dynamic EC2 inventory
1. Hardening server
  * Change ssh port
2. Dynamic SSH port validation



## Testing

For local testing purpose a vagrant config is added. First add roles in `tests/playbook.yml`. Start vagrant machine.

```bash
vagrant up
```
