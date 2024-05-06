#Additional RKE2 Control Plane Node - Ansible Role

Description:

Bootstraps one or more additional RKE2 Control plane nodes.

Use this role:

You should already have another running RKE2 Control plane node.

Specify your server token in vars or add something like this to your playbook.

```
- name: Install RKE2 Initial Control plane
  gather_facts: true
  become: true
  hosts: rke2_initial_control_plane
  roles:
    - initial_rke2_control_plane
  tags:
    - initial
  tasks:
    - name: slurp the server token
      ansible.builtin.slurp: 
        src: /var/lib/rancher/rke2/server/token
      register: server_token
```