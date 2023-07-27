Role Name
=========

Ansible Role to install Kubernetes on RedHat, Centos, Amazon Linux based machines

Requirements
------------

Any Container Runtime Interface like Docker, Containerd, CRI-O must be installed

Example : ansible-galaxy install role pradeepkumar027.containerd

Refer [ansible-role-containerd](https://github.com/pradeepkumar027/ansible-role-containerd/tree/develop)

Role Variables
--------------

"kubernetes_role" variable must be defined explicitly when using the role. Allowed values ["controlplane","node"]

See `defaults/main.yml`

Dependencies
------------

None

Example Playbook
----------------

    - name: install containerd
      hosts: all
      roles:
      - pradeepkumar027.containerd
    - name: install kubernetes on controlplane
      hosts: k8s-controlplane
      become: true
      vars:
        kubernetes_role: controlplane
      roles:
      - pradeepkumar027.kubernetes
    - name: install kubernetes on nodes
      hosts: k8s-node01
      become: true
      vars:
        kubernetes_role: node
      roles:
      - pradeepkumar027.kubernetes

License
-------

BSD

Author Information
------------------

Role created by Pradeep Kumar