[![Build Status](https://travis-ci.org/sky-joker/ansible-vmware-govcsim-provisioner.svg?branch=master)](https://travis-ci.org/sky-joker/ansible-vmware-govcsim-provisioner) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# Ansible VMware govcsim provisioner

This Role provisions a container for [vcsim](https://github.com/vmware/govmomi/tree/master/vcsim) that is created in the Go language.

## Requirements

* docker-compose

## Install

How to install this role run following command.

```
$ ansible-galaxy install sky_joker.ansible_vmware_govcsim_provisioner -p roles
```

## Role Variables

You can change the configuration of the vcsim to be provisioned by changing the variable.  
Available variables are(see `defaults/main.yml`):

```yaml
---
# govcsim container params.
# please choices 'started' or 'absent' for the state.
govcsim_image: quay.io/ansible/vcenter-test-container:latest
state: started

# govcsim params.
app: 0
cluster: 0
dc: 1
ds: 1
folder: 1
host: 3
pg: 1
pod: 1
pool: 1
vm: 2
```

|     param     |                                description                                 |
|---------------|----------------------------------------------------------------------------|
| govcsim_image | [vcsim container image](https://github.com/ansible/vcenter-test-container) |
| state         | choices started or absent                                                  |
| app           | Number of virtual apps per compute resource                                |
| cluster       | Number of clusters                                                         |
| dc            | Number of datacenters                                                      |
| ds            | Number of local datastores                                                 |
| folder        | Number of folders                                                          |
| host          | Number of standalone hosts                                                 |
| pg            | Number of port groups                                                      |
| pod           | Number of storage pods per datacenter                                      |
| pool          | Number of resource pools per compute resource                              |
| vm            | Number of virtual machines per resource pool                               |

## Dependencies

None.

## Example Playbook

```yaml
---
- name: vcsim provisioning playbook
  hosts: localhost
  gather_facts: no
  roles:
    - sky_joker.ansible_vmware_govcsim_provisioner
```

## License

MIT

## Author Information

This role was created by [sky-joker](https://github.com/sky-joker).
