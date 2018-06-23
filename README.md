# Presentation

This ansible project is for persons who are looking for a deployment of Apache Flink as a cluster.




# Before starting

Edit the host.ini file:
```
nano playbooks/inventory/host.ini
```
Then, remove and replace:
* **jobmanager_servers** by the server name that will be used as a master
* **taskmanager_servers** by the list of servers that will be used as slaves (one server name by line)

The ansible will download, configure and launch the Apache Flink cluster. A default configuration file is provided:

```
nano playbooks/group_vars/all/config.yml
```




# Deploy Apache Flink cluster

```
cd playbooks
ansible-playbook -i inventory/host.ini deploy.yml
```

After the deployment, you will be able to access the Apache Flink web interface in your browser:

```
http:<ip_addr_jobmanager>:8081
```




# Flink service

During the deployment, a service is set for flink. you can use systemctl to manage the cluster:

```
systemctl ( start | stop | restart | ... ) flink
```
