Ansible Role: Solr
=========

Installs and configures the Apache Solr search platform.

Requirements
------------

Java - the current version of Solr (6.x) requires Java Runtime Environment (JRE) version 1.8 or higher.

Role Variables
--------------

    solr_major_version:         8
    solr_minor_version:         11
    solr_patch_version:         1
    solr_version:               "{{ solr_major_version }}.{{ solr_minor_version }}.{{ solr_patch_version }}"
    solr_install_dir:           "/opt"
    solr_var_dir:               "/var/solr"
    solr_service:               "solr"
    solr_port:                  "8983"

NOTE: if there are upgrade steps required for existing indices, this role will not undertake them

    solr_upgrade:               true
    solr_upgrade_arg:           "-f"
    solr_download_dir:          "{{ ansible_env.HOME}}"
    solr_dir:                   "solr-{{ solr_version }}"
    solr_download_file:         "{{ solr_dir }}.tgz"
    solr_install_script:        "install_solr_service.sh"
    solr_download_url:          "https://archive.apache.org/dist/lucene/solr/{{ solr_version }}/{{ solr_download_file }}"
    solr_checksum_algo:         "sha1"
    solr_checksum_url:          "{{ solr_download_url }}.{{ solr_checksum_algo }}"
    solr_bin:                   "{{ solr_install_dir }}/{{ solr_service }}/bin"
    solr_home:                  "{{ solr_var_dir }}/data"
    solr_cores:                 []
    # user vars
    solr_user:                  "solr"
    solr_group:                 "{{ solr_user }}"

uid & gid are available for override, but we don't define them by default

    # solr_user_uid:
    # solr_group_gid:

To override all the environment vars, provide a template similar to the provided example and set the following with its filename:

    solr_env_template:          ""

To set individual environment vars, provide them like so:

    solr_env_vars:             
    - var:    "SOLR_HEAP"
      value:  "2g"

Dependencies
------------

Any role (or other method) that will provide Java 8 (JRE 1.8).

Example Playbook
----------------

    - hosts: solr
      roles:
         - { role: java }
         - { role: solr }

License
-------

CC0

Author Information
------------------

Drew Heles
