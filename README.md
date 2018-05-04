## Wireguard ansible playbook

### Requarements

Debian/ubuntu on remote hosts
Redhat/centos need to test

### Install

### how to use

Change hosts file:

```
[vpn]

anyname1 	ansible_host=<public_ip_1> 	vpn_ip=10.200.0.1 	site_net=<local_subnet_1>
anyname2 	ansible_host=<public_ip_2> 	vpn_ip=10.200.0.2 	site_net=<local_subnet_2>
```

I'm using DigitalOcean droplets in different regions,
So if droplets in the same DC then traffic don't route in tunnel else I make route to IP address of eth1 interface over wireguard tunnel

You can replace in template wg0.conf.j2

> AllowedIPs = {{ hostvars[host]['vpn_ip'] }}/32 {% if site_net != hostvars[host]['site_net'] %}, **{{ hostvars[host]['ansible_eth1'].ipv4.address }}** {% endif %} 

 **hostvars[host]['site_net']**

this will make routes for marked subnets over tunnels but will not working if hosts has same subnet. 

Still in progress...


```
ansible-playbook full-mesh.yml
```