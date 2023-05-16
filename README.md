# What is this?
This is a highly available K3S Cluster setup via Ansible. 
This will setup the cluster in an automated fashion.

Note: Since this is a test lab, I don't really care about any password leaks, as they will never be used for reals. 


### Dev Environment
- Beefy Workstation (Fedora 37, AMD 5950x, 128GB RAM)
- Ansible
- Docker
- VMWare Workstation Pro (this just works better than libvirt and VirtualBox IMHO)
- Molecule  (https://molecule.readthedocs.io/en/latest/installation/)  

### Test Environment
- Proxmox VM Host
- Dual E5-2690v4
- 192GB RAM
- 1TB NVMe Storage

### Anisble Lab  
Here's a list of VMs I have created
```
10.107.0.110 
10.107.0.111 k3s-control-01 k3s-control-01.cloud.skyline.lan
10.107.0.112 k3s-control-02 k3s-control-02.cloud.skyline.lan
10.107.0.113 k3s-control-01k3s-control-03.cloud.skyline.lan
10.107.0.121 k3s-node-01 k3s-node-01.cloud.skyline.lan
10.107.0.122 k3s-node-02 k3s-node-02.cloud.skyline.lan
10.107.0.123 k3s-node-03 k3s-node-03.cloud.skyline.lan
10.107.0.130-139 Public IP
```

Each Control Node VM has 2 CPUS, 2GB RAM, and 40GB Disk. Each Worker Node VM has 4 CPUS, 4GB RAM, and 100GB Disk. Also each one is Rocky Linux 9


#### Anisble Notes:
##### Create new role
```
molecule init role beer30.k3s -d docker
```

##### Collections Installed
ansible-galaxy collection install ansible.posix




##### Molecule Cheat Sheet
https://molecule.readthedocs.io
- molecule create
- molecule converge
- molecule login
- molecule destroy

##### Run Playbook
ansible-playbook -i hosts.ini bootstrap.yml



## Notes:


## Running Ansible without typing in the vault password all the damn time
1. Create a file ~/.ansible/ansible-pass (Shuld be just a one liner with the password)
2. export ANSIBLE_VAULT_PASSWORD_FILE=~/.ansible/ansible-pass pointing to this file   ANSIBLE_VAULT_PASSWORD_FILE=~/.ansible/ansible-pass

