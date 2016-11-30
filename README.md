Role Name
=========

This role installs and configures Entrada by SIDN ( http://entrada.sidnlabs.nl/ ) 

Requirements
------------

This role must be run on a node which is already part of the cloudera hadoop cluster.
`impala-shell` and `hdfs` must be installed.

Role Variables
--------------

 * `entrada_nameservers`: list of nameserver names, required
 * `entrada_version` : Version number, determines the download url and creates the correct symlink for entrada-latest
 * `entrada_download_url`: download url for the entrada source, determined from 
 * `entrada_user`: system user which runs all the entrada scripts
 * `entrada_group`: group for the entrada system user
 * `entrada_user_home`: homedir for the entrada system user
 * `entrada_cronjobs_disabled`: set to yes to disable all entrada jobs
 * `entrada_config_*`: all configuration variables that go to config.sh, also affects the places where this role downloads entrada, configures folders etc
 * `èntrada_settings_*`: settings that go into entrada-settings.properties

Dependencies
------------

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: entrada_management_nodes
      roles:
         - { role: ansible-role-entrada, entrada_nameservers: ['ns1.example.com', 'ns2.example.com' ] }

License
-------

BSD

Author Information
------------------

