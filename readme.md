huaweicloud.huaweicloud_modules
=========

This role includes the latest changes and bug fixes for Azure modules from the `devel` branch of [Ansible repository](https://github.com/ansible/ansible). If you cannot wait for Ansible's next release, installing this role is a good choice. 

Prerequisite
------------

The usage of this playbook role assumes that you've already setup an Ansible environment for Azure. For details, please refer to Ansible tutorial [Getting Started with Azure](http://docs.ansible.com/ansible/latest/guide_azure.html). 


Installation
------------

Install the role.

  ``` bash
  $ ansible-galaxy install huaweicloud.huaweicloud_modules
  ```

Example Playbook
----------------

    - hosts: localhost
      roles:
        - { role: huaweicloud.huaweicloud_modules }
      tasks:
		- name: create a new vm
		  hwc_compute_instance:
			identity_endpoint: "https://iam.cn-north-1.myhwclouds.com/v3"
			user_name: "{{ user_name }}"
			password: "{{ password }}"
			domain_name: "{{ domain_name }}"
			project_name: "{{ project_name }}"
			region: "{{ region }}"
			log_file: "/tmp/vm.log"

			name: "{{ vm_name }}"
			image: "{{ image_id }}"
			flavor: "{{ flavor_id }}"
			networks:
			  - uuid: "{{ network_id }}"
		  register: vm 
		- name: dump the output
		  debug:
			msg: '{{ vm }}'

License
-------
MIT
