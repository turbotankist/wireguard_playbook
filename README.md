## Wireguard ansible playbook

### Requarements

Debian/ubuntu on remote hosts
Redhat/centos need to test

### Install

### how to use

Change hosts file:

```
[vpn]

anyname1 	ansible_host=<public_ip_1> 	vpn_ip=10.200.0.1
anyname2 	ansible_host=<public_ip_2> 	vpn_ip=10.200.0.2  add_routes="10.10.1.0/24, 10.20.1.0/24"
```


```
ansible-playbook full-mesh.yml
```