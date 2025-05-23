# foreman-setup

NREC foreman setup with ansible. Should be part of norcams/ansible with time. 

This repo should already be checked out on `admin-01` at `/root/foreman-setup`

### Install

Use python 3.9+ and virtualenv to install ansible:

```bash
python3.11 -m venv .
source bin/activate
pip install --upgrade pip
pip install -r requirements.txt
ansible-galaxy install -r requirements.yaml
```

Tested on el8 with python 3.11 and el9 with python 3.12

## Updated dependencies

Update foreman role:

``` bash
source bin/activate
ansible-galaxy install -r foreman_role.yaml --force
```

Update all roles and collections

``` bash
source bin/activate
ansible-galaxy install -r requirements.yaml --force
```

To change version for other roles and collections with pined versions edit
`requirements.yaml` first.

## Run foreman setup

``` bash
source bin/activate
ansible-playbook -i <path to inventory> playbooks/foreman_setup.yaml [--check]
```

We can symlink `<loc>.inventory` to inventory to avoid using the `-i` option.

### Run only some tasks

You can run only some task by using `--tags <tag>`. To get a list of all current tags run:

``` bash
grep -r tags .roles/foreman/tasks/* | awk '{ print $3 }'
```

## Run other tasks with sudo

If you need to run a ansible playbook with sudo you will have to use the full path
since sudo does not use the python virtual env. You can also create an alias and run
`ansible-playbook` without implicit sudo:

``` bash
alias ansible-playbook="sudo $(which ansible-playbook)"
```
