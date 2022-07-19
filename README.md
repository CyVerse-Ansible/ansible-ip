# ansible-ip
[![Ansible Galaxy](https://img.shields.io/badge/role-cyverse--ansible.ip-blue.svg)](https://galaxy.ansible.com/cyverse-ansible/ip/)

An ansible role for using the ip command to manipulate devices, policies, routing, and tunnels.

At the moment, it only works with network devices. It can only bring up or down a given device, set 
or unset the NOARP flag, and change a device's transmit queue length. In the future, it should be 
expanded to support all of the features of the `ip` command.

## Requirements

The hosts need to have libselinux-python installed.

## Role Variables

Variable                  | Required | Default                               | Choices     | Comments
------------------------- | -------- | ------------------------------------- | ----------- | --------
`ip_link_arp`             | no       |                                       | true, false | if present, whether or not to enable ARP
`ip_link_mtu`             | no       |                                       |             | if present, then new MTU
`ip_link_name`            | no       | `ansible_default_ipv4.alias`          |             | the name of the network device to modify
`ip_link_txqueuelen`      | no       |                                       |             | if present, the new transmit queue length
`ip_link_up`              | no       |                                       | no, yes     | if present, whether or not the device is to be up
`ip_netplan_mtu_file`     | no       | /etc/netplan/50-mtu.yaml              |             | if `ip_link_mtu` is present, and the managed node runs Ubuntu >= 20.04, this is the file used to persist the new MTU
`ip_udev_txqueuelen_file` | no       | /etc/udev/rules.d/50-txqueuelen.rules |             | if `ip_link_txqueuelen` is present, and the managed node runes Ubuntu >= 20.04, this is the file used to persist the new txqueuelen

## Dependencies

None

## Example Playbook
```yaml
- hosts: 10000Mbit/s
  become: true
  roles:
    - role: CyVerse_Ansible.ip
      ip_link_txqueuelen: 10000
```

## License

See [license](/LICENSE.txt).

## Author Information

Tony Edgin  
<tedgin@cyverse.org>  
[CyVerse](https://cyverse.org)
