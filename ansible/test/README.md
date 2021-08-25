# Centos7 Base AMI testing

### Docker for quicker tests
A simple docker setup to cover testing of Ansible.

To test, first ensure you have all required dependancies installed: 
```
ansible-galaxy install -r requirements.yml
ansible-galaxy install -r ../requirements.yml
```

Then we can execute the playbook. This will create a docker container based on Centos7 and execute the playbook.
```
ansible-playbook playbook.yml --extra-vars @../host_vars/centos7-base.yml --skip-tags rule_4.3
```

### Vagrant for more thorough tests

Testing for this image has been set up using Vagrant due to the requirement to test plays that are not compatible with Docker hosted instances (e.g. SELinux, AV)

To test, run `vagrant up` from this directory. This will create a virtual machine based on Amazon Linux 2 and automatically run the Ansible provisioner.

To re-run tests, run `vagrant provision`

When finished, run `vagrant destroy`, which will destroy the currently running VM and cleanup.
