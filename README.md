l3o.guacamole_pod
=================

This Ansible role setups a apache guacamole container using podman.

Role Variables
--------------

| Variable                            | Value                                               |
| ----------------------------------- | --------------------------------------------------- |
| ``ldap_hostname``                   | ``ldap.example.com``                                |
| ``ldap_port``                       | ``389``                                             |
| ``ldap_encryption_method``          | ``starttls`` (default), ``ssl`` or ``none``         |
| ``ldap_config_base_dn``             | ``cn=guac,dc=example,dc=com``                       |
| ``ldap_user_base_dn``               | ``ou=People,dc=example,dc=com``                     |
| ``ldap_group_base_dn``              | ``ou=Groups,dc=example,dc=com``                     |
| ``guacamole_extensions``            | ``[]`` (default), each entry is a path to either a extension jar file or directory |
| ``guacamole_volume_host_path``      | ``/tmp/guacamole``                                  |
| ``guacamole_host_port``             | ``8080`` (default)                                  |
| ``guacamole_guacd_image``           |  ``docker.io/guacamole/guacd:latest`` (default)     |
| ``guacamole_web_image``             |  ``docker.io/guacamole/guacamole:latest`` (default) |
| ``pod_yaml_dir``                    | ``/etc/containers/pods`` (default)                  |
| ``pod_name``                        | ``guacamole`` (default)                             |
| ``pod_label``                       | ``guacamole`` (default)                             |
| ``container_state``                 | ``present`` (default) or ``absent``                 |

Dependencies
------------

* [ikke_t.podman_container_systemd](https://galaxy.ansible.com/ikke_t/podman_container_systemd)

Example Playbook
----------------

The following playbook setups a apache guacamole container using a ldap
directory at ``ldap.example.com``:

    - hosts: all
      tasks:
        - include_role:
            name: l3o.guacamole_pod
        vars:
          ldap_hostname: ldap.example.com
          ldap_port: 636
          ldap_config_base_dn: cn=guac,dc=example,dc=com
          ldap_user_base_dn: ou=People,dc=example,dc=com
          ldap_group_base_dn: ou=Groups,dc=example,dc=com

License
-------

GPLv3+

Author Information
------------------

Christian Felder
