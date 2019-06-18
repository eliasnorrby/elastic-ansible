# Elastic stack setup using Ansible

This is a proof-of-concept / sandbox solution for provisioning the Elastic stack (Elasticsearch, Kibana, Logstash, Filebeat) on a server running Centos7.

Your local machine is used as the ansible control unit.

To demo it, first spin up the VMs using vagrant with `vagrant up`. 

To setup users required for the provisioning, run

```sh
ansible-playbook bootstrap.yml --tags "initial_bootstrap,all"
```

This sets up the `deploy` user with passwordless sudo for use during the rest of the provisioning.

Next, run:

```sh
ansible-playbook wip.yml
```

When your done, browse to `192.168.88.201:8008` (or whatever IP you Centos server is running on) and you will find a running kibana instance with some sample dashboards set up.
