# Presentation

This ansible project is a deployment of Apache Flink as a cluster.




# Before starting

Edit the host.ini file:
```
nano playbooks/inventory/host.ini
```
Then, remove and replace:
* **jobmanager_servers** by the server name that will be used as a master
* **taskmanager_servers** by the list of servers that will be used as slaves (one server name by line)

A default configuration file is provided with variables that are used for the project:

```
nano playbooks/group_vars/all/config.yml
```

The playbook downloads Java8 and Apache Flink archive, sets the configuration, creates an alias and a flink systemd service.




# Deploy Apache Flink cluster

```
cd playbooks
ansible-playbook -i inventory/host.ini deploy.yml
```

After the deployment, you can access the Apache Flink web interface in your browser:

```
http:<ip_addr_jobmanager>:8081
```




# Flink service

During the deployment, a service is set for flink. you can use systemctl to manage the cluster:

```
systemctl ( start | stop | restart | ... ) flink
```




# FLink alias

A "flink" alias is created inside the .rc file of the shell you informed in config.yml
