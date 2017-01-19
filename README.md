Ansible Role: virtualbox-desktop-guest
=====================

Build status for this role: [![Build Status](https://travis-ci.org/fridanellros/ansible-role-virtualbox-desktop-guest.svg)](https://travis-ci.org/fridanellros/ansible-role-virtualbox-desktop-guest)

This role downloads, installs and configures the requested VirtualBox guest additions with x11 support. Tailored for running on localhost with local connection. 

Requirements
------------

None, all prerequisites will be installed (and can be removed afterwards). If you don't set the **virtualbox_keep** variable to true, all packages that were installed for building will be removed (the installed packages will be exactly the same as before executing the role).
  - bzip2
  - dkms
  - gcc
  - make
  - linux-headers


Role Variables
--------------

Available variables are listed below, along with default values

**virtualbox_keep**: A boolean stating whether the packages necessary for compiling should be kept on the system. If not specified, defaults to no.

**virtualbox_remove_os_packages**: A boolean stating whether to remove any previously installed VirtualBox packages. If not specified, defaults to no.

**virtualbox_version**: The requested version of VirtualBox. If the current version does not match that version, it will try to (re)install VirtualBox guest additions. If set to `auto`, it will try to determine the VirtualBox version of the host system. The defaults can be found in ```defaults/main.yml```. Note: This will not work running on the guest!
```
virtualbox_version: auto
```

**virtualbox_x11**: A boolean stating whether VirtualBox guest additions will be compiled with x11 support. If not specified, defaults to no.



Dependencies
------------

None.



Example Playbook
----------------
```
- hosts: localhost
  connection: local
  become: yes
  roles:
    - {role: fridanellros.virtualbox-desktop-guest, virtualbox_version: x.y.zz}
```
This example will install VirtualBox guest additions, and will not keep the build packages to the system if they needed to be installed for this role.


License
-------

GPLv3


Author Information
------------------

Adapted/forked by Frida Nellros .

Original created by Peter Mosmans, with contributions by Isaac Kim and Fred Leger.
