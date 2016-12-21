Ansible Role: Solr
=========

Installs and configures the Apache Solr search platform.

Thus far, very minimal. If you need much in the way of configuration, you may wish to either use another role that's further along or contribute (code or suggestions) to this one.

Requirements
------------

Java - the current version of Solr (6.x) requires Java Runtime Environment (JRE) version 1.8 or higher.

Role Variables
--------------

    java_version:         1.8
    solr_version:         6.2.1
    solr_install_dir:     "/opt"
    solr_download_dir:    "{{ ansible_env.HOME}}"
    solr_dir:             "solr-{{ solr_version }}"
    solr_download_file:   "{{ solr_dir }}.tgz"
    solr_install_script:  "install_solr_service.sh"
    solr_url:             "https://archive.apache.org/dist/lucene/solr/{{ solr_version }}/{{ solr_download_file }}"
    solr_checksum_algo:   "sha1"
    solr_checksum_url:    "{{ solr_url }}.{{ solr_checksum_algo }}"

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
