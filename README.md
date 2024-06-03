## foreman-setup

NREC foreman setup with ansible. Should be part of norcams/ansible with time.

### Install

Use python 3.9+ and virtualenv to install ansible

Tested on el8 with python 3.11.

## Run only some tasks

You can run only some task by using `--tags <tag>`. To get a list of all current tags run:

``` bash
grep -r tags .roles/foreman/tasks/* | awk '{ print $3 }'
```

## Run with sudo

If you need to run the ansible playbook with sudo you will have to use the full path
since sudo does not use the python virtual env. You can also create an alias and run
`ansible-playbook` without implicit sudo:

``` bash
alias ansible-playbook="sudo $(which ansible-playbook)"
```
