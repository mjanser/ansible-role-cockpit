# Ansible Role: cockpit

An Ansible role that installs cockpit on Fedora.

## Requirements

Nginx needs to be installed beforehand. To achieve this the following roles could be used:
- mjanser.nginx

## Role Variables

Available variables are listed below, along with default values:

    cockpit_server_name: example.com
    cockpit_port: 9090
    cockpit_allowed_network: "{{ ansible_default_ipv4.network|default('192.168.1.0') }}/{{ ('192.168.1.0/' ~ ansible_default_ipv4.netmask|default('255.255.255.0'))|ipaddr('prefix') }}"

### Virtual host

The nginx virtual host can be configured with the variables `cockpit_server_name`, it listens on port 80.

Access to the virtual host is restricted to the network defined in the variable `cockpit_allowed_network`.
The default value is the network of the default IPv4 interface, which needs `python-netaddr` to be installed on the host which runs ansible.

### Port

The variable `cockpit_port` defines the port which the cockpit service will use.

## Dependencies

None

## Example Playbook

    - hosts: all
      roles:
        - { role: mjanser.cockpit }

## License

MIT
