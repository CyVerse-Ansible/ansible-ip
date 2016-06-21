# ansible-ip
[![Build Status](https://travis-ci.org/cyverse/ansible-ip.svg?branch=master)](https://travis-ci.org/cyverse/ansible-ip)

An ansible role for using the ip command to manipulate devices, policies, routing, and tunnels.

At the moment, it can only be used to set the transmission queue length for a given link to a NIC. In the future, it should be expanded to support all of the features of the `ip` command.


## Requirements

None


## Role Variables

| Variable           | Required | Default                        | Choices | Comments |
| ------------------ | -------- | ------------------------------ | ------- | -------- |
| ip_link_name       | no       | {{ansible_default_ipv4.alias}} |         | The link to the NIC to be tuned |
| ip_link_txqueuelen | no       | 1000                           |         | The number of packets the transmission queue the NIC's transmission will hold |


## Dependencies

None


## Example Playbook
```yaml
- hosts: 10000Mb/s
  become: true
  gather_facts: true
  roles:
    - role: ansible-ip
      ip_link_txqueuelen: 10000
```

## License

BSD


## Author Information

Tony Edgin

