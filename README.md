Role Name
=========

This role is to deploy kubernetes cluster on master and worker nodes with Ubuntu server (Tested on Ubuntu 16.04 LTS) using Ansible version 2.9.10

Requirements
------------
Ansible:  2.9.10

OS: Ubuntu 16.04 LTS


Master node setup: Follwoing two steps are required before deploying role for master nodes

	Step1: Cluster Installation User: (Default installation user is root) | to change default user run below commands after downloading roles and replace your user_name in below command, make usre to add sudo user
			    		sed -i s/root/user_name/g /etc/ansible/roles/kubernetes-cluster/tasks/*

	Step2:Setting IP for kubernetes master node:
   
				sed -i s/192.168.56.10/master_node_IP/g  /etc/ansible/roles/kubernetes-cluster/tasks/initialize-kubernetes-cluster.yaml


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

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
