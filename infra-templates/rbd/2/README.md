## Rancher RBD

> **Note:** v0.1.0 and v0.1.1 These items currently only supports Ceph `Jewel` version. Due to librbd compatibility with the kernel, it is recommended to use Ubuntu16.04 for host OS.  
v0.1.2 Uses a CentOS base ceph image based on v12 Ceph. This version adds support for ceph usernames as well.

### Default Configuration

As we all know, Ceph's configuration file is very complex, so it is difficult to automatically generate it. 
You need to manually synchronize the configuration file in the `/etc/ceph` directory on all rancher-agent nodes, rancher-rbd will mount this directory.

Use case:
```
version: '2'
services:
  foo:
    image: nginx
    volumes:
    - bar:/var/lib/storage
volumes:
  bar:
    driver: rancher-rbd
    driver_opts:
      size: 2G
      pool: rbd
      user: myDevUser
```
