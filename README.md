# ansible-ip
[![Build Status](https://travis-ci.org/CyVerse-Ansible/ansible-ip.svg?branch=master)](https://travis-ci.org/CyVerse-Ansible/ansible-ip)

An ansible role for using the ip command to manipulate devices, policies, routing, and tunnels.

At the moment, it only works with network devices. It can only bring up or down a given device, set or unset the NOARP flag, and change a device's transmit queue length. In the future, it should be expanded to support all of the features of the `ip` command.


## Requirements

The hosts need to have libselinux-python installed.


## Role Variables

Variable             | Required | Default                      | Choices     | Comments
-------------------- | -------- | ---------------------------- | ----------- | --------
`ip_link_arp`        | no       |                              | true, false | whether or not to enable ARP
`ip_link_name`       | no       | `ansible_default_ipv4.alias` |             | the name of the network device to modify
`ip_link_txqueuelen` | no       |                              |             | if present, the new transmit queue length
`ip_link_up`         | no       |                              | no, yes     | if present, whether or not the device is to be up


## Dependencies

None


## Example Playbook
```yaml
- hosts: 10000Mbit/s
  become: true
  roles:
    - role: CyVerse-Ansible.ip
      ip_link_txqueuelen: 10000
```

## License

BSD


## Author Information

Tony Edgin

