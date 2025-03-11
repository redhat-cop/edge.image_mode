bootc\_builder\_prepare
=====================

A role to prepare a RHEL server for building image build containers (aka bootc)

Requirements
------------

A server with RHEL 9, and access to the necessary repositories (see [vars](vars/main.yml)).

Role Variables
--------------

See [defaults](defaults/main.yml).

Dependencies
------------

- `fedora.linux_system_roles` or `redhat.rhel_system_roles` (configurable)

Example Playbook
----------------

    - hosts: bootc_builders
      roles:
         - role: imode_prepare

License
-------

BSD

Author Information
------------------

Eric Lavarde <elavarde@redhat.com>
