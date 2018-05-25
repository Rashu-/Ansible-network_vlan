# Network vlans configuration

Ansible role that configures vlans for networking devices. 

The configuration of the role is done so that it shouldn't be necessary to modify the role for any configuration.
All settings can be configured by changing role parameters or by declaring new config as variable.

Please report any issues or send PR.

## Examples

```yaml
---

- name: Example of how to add a vlan
  hosts: switches
  vars:
    vlans:  
      - id: 10
        name: data
        state: present
        admin_state: up
  roles:
    - Ansible-network_vlan

- name: Example of how to add many vlans with no specific per vlan details like name and admin state
  hosts: switches
  vars:
    vlan_range: 
  - ids: 10,122-128,422-444
    state: present
  roles:
    - Ansible-network_vlan


- name: Example of how to remove a vlan
  hosts: switches
  vars:
    vlans:  
      - id: 10        
        state: absent        
  roles:
    - Ansible-network_vlan

- name: Example of how to remove many vlans easy
  hosts: switches
  vars:
    vlan_range: 
  - ids: 10,122-128,422-444
    state: absent
  roles:
    - Ansible-network_vlan

```

## Role variables

```yaml
# Define the vlan range to be configured, use this for quick configuration of multiple vlans (see README for examples)
vlan_range: { }

# Define the vlans to be configured (see README for examples)
vlans: { }
```


## License

Apache


## Author

Dan Murarasu
