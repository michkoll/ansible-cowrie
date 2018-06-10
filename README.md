# ansible-cowrie
Setup a honeypot on aws EC2 instance

## Install ansible roles

Before running the playbook you have to install the ansible roles used in this playbook. The roles should be installed the `roles/` directory.

```bash
ansible-galaxy install --force --roles-path roles/ -r requirements.yml
```

## Testing

For local testing purpose a vagrant config is added. First add roles in `tests/playbook.yml`. Start vagrant machine.

```bash
vagrant up
```
