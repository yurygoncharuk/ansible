# Ansible Zabbix monitoring for Mirantis OpenStack


## Roles:

--------------------------------------------------------------------------------
### 1. altoros.zabbix-agent.install

Installing and configuration of the Zabbix agent. Uses packages from http://www.zabbix.com.

--------------------------------------------------------------------------------
### 2. altoros.zabbix-agent.configure

Getting some information from controller's files for configuring templates.
Adding configs, scripts for monitoring OpenStack's services and installing some dependency for it.

#### Requirements for role

1) Create OpenStack user for monitoring and add it to project `services`

2) Update vars:
- openstack_user: created user
- openstack_pass: created password for this user
- mgmt_ip: update interface name if it necessary
- host_net: update interface name if it necessary

--------------------------------------------------------------------------------
### 3. altoros.zabbix-server.configure

Creating a new host or updating an existing in Zabbix server
Creating a new macro for host or updating an existing in Zabbix server

#### Requirements for role

1) Import `zabbix_openstack_tmpl.xml` to Zabbix server

2) Install `zabbix-api` on ansible master node

    pip install zabbix-api
  
3) Update vars:
- zabbix_server: url for your Zabbix server
- zabbix_user: zabbix server user
- zabbix_pass: user's password
- host_ip: update interface name if it necessary
- mgmt_ip: update interface name if it necessary
- public_ip: update interface name if it necessary
- storage_ip: update interface name if it necessary