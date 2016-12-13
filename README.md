SIDN Entrada Ansible Role
=========================

This role installs and configures Entrada by SIDN on a cloudera hadoop cluster node ( http://entrada.sidnlabs.nl/ ) by performing the steps listed on http://entrada.sidnlabs.nl/docs/introduction/install/ :

 * Install dependencies (Java, Parallel, Kerberos client)
 * Create entrada user/group
 * Download / unpack entrada and symlink 'entrada-latest'
 * Create log directory and configure log rotation
 * Create directories for incoming pcaps
 * Create hdfs dir 
 * Create impala tables
 * Set up cron jobs
 

Requirements
------------

This role must be run on a node which is already part of the cloudera hadoop cluster.
`impala-shell` and `hdfs` must be installed.

Role Variables
--------------

see `defaults/main.yml` for the full list

 * `entrada_nameservers`: list of nameserver names. This is the only variable that **must** be set, all others have defaults.
 * `entrada_version` : Version number, determines the download url and creates the correct symlink for entrada-latest
 * `entrada_download_url`: download url for the entrada source, determined from `entrada_version` 
 * `entrada_user`: system user which runs all the entrada scripts
 * `entrada_group`: group for the entrada system user
 * `entrada_user_home`: homedir for the entrada system user
 * `entrada_cronjobs_disabled`: set to yes to disable all entrada jobs
 * `entrada_config_*`: all configuration variables that go to config.sh, also affects the places where this role downloads entrada, configures folders etc
 * `entrada_settings_*`: settings that go into entrada-settings.properties

Dependencies
------------

Example Playbook
----------------

    - hosts: entrada_management_nodes
      roles:
         - { role: ansible-role-entrada, entrada_nameservers: ['ns1.example.com', 'ns2.example.com' ] }

