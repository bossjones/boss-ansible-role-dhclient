# boss-ansible-role-dhclient
Ansible role to setup Dynamic Host Configuration Protocol Client

## Requirements

None

## Role Variables

Available variables are listed below, along with default values:

    dhclient: {}

## Dependencies

None

## Example Playbook

    - hosts: servers
      roles:
        - role: linuxhq.dhclient
          dhclient:
            - interface: "{{ ansible_default_ipv4.address }}"
              settings:
                prepend:
                  domain-name-servers:
                    - 1.1.1.1
                    - 1.0.0.1
                request:
                  - broadcast-address
                  - domain-name
                  - domain-name-servers
                  - host-name
                  - routers
                  - subnet-mask
                require:
                  - domain-name-severs
                  - subnet-mask
                supersede:
                  host-name: dhcp.linuxhq.org
                  domain-name: linuxhq.org


# Inspiration
- https://github.com/linuxhq/ansible-role-dhclient
