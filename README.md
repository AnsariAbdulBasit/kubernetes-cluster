Role Name
=========

This role is to deploy kubernetes cluster on master/worker nodes with Ubuntu server (Tested on Ubuntu 16.04 LTS) using Ansible version 2.9.10

For master node deployment : Changes of IP address explained in Requirements section

For worker node deployment : Variables changes explaind in Role Variables section

Requirements
------------
Ansible:  2.9.10

OS: Ubuntu 16.04 LTS


Master node setup: Master node server IP needs to change using below step and installation user (optional)



Setting IP for kubernetes master node:
   
	sed -i s/192.168.56.10/master_node_IP/g  /etc/ansible/roles/kubernetes-cluster/tasks/initialize-kubernetes-cluster.yaml

Optional: Changing Cluster Installation User: (Default installation user is root) | to change default user run below commands after downloading roles and replace your user_name in below command, make sure to add sudo user only.

        sed -i s/root/user_name/g /etc/ansible/roles/kubernetes-cluster/tasks/*


Worker node setup: Variables changes required for worker node setup mentioned below in Role Variables section


Role Variables
--------------

Same role can be used to deploy worker node by disaling below steps in defaults/main.yml

Worker node setup: Edit defaults/main.yml file and false below variables

			vi /etc/ansible/roles/kubernetes-cluster/defaults/main.yml

			   initialize_kubernetes: False
			   Setup_kube_config: False
			   setup_container_networking: False
			   generate_kube_join_command: False


Dependencies
------------

No other role Dependencies

Example Playbook
----------------

Downloading the role from ansible galaxy

	ansible-galaxy install ansariabdulbasit.kubernetes_cluste

Creating Playbook.yaml file

	---
	- hosts: target1
	  become: true
	  roles:
	      - kubernetes-cluster

Creating Inventory.yaml file with master/worker hosts

	target1 ansible_host=192.168.56.10 ansible_ssh_pass=PASSWORD

License
-------

Free


Author Information
------------------

This rol is created by Abdul Basit

https://www.linkedin.com/in/abdul-basit-ansari-b05b31a8/
