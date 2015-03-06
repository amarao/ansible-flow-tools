flow-tools
=========

Installs and configures packet flow-tools (to capture netflow). This playbook covers only flow-capture settings (no filters)

Requirements
------------

Ansible 1.6+

Role Variables
--------------

flowtools.captures contains list of captures to configure. Each capture should could have options and binding settings, and must have
workdir.

Binding settings:
* localip
* remoteip
* port

Options:
* byte_order
* debug_level
* expire_count
* expire_size
* iter_name
* filter_definition
* rotations
* netsting_level
* start_interval
* tag_name
* active_def
* pdu_version
* xlate_fname
* z_level

All options names are taken 'as is' from man flow-capture.

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:


    - hosts: collectors
      vars:
        captures:
         -
           workdir: '/srv/router1'
         -
           workdir: '/srv/router2'
           port: 9999
         -
           workdir: '/srv/router3'
           localip: 10.0.0.1
           remoteip: 10.0.0.2
           port 5000
           options:
               debuglevel: 4
               pdu_version: 5
               z_level: 9
               expire_size: 16M
      roles:
         - role: flow-tools

License
-------

BSD

Author Information
------------------

(c) George Shuklin, 2015
