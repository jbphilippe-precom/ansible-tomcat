Role Name
=========

Tomcat 8 installation (configuration needs to be improved).

Requirements
------------

- Ubuntu Xenial
- Ansible 2.1+

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Role Variables
--------------

    tomcat_port: 8080
    tomcat_bind_address: "127.0.0.1"

    tomcat_use_lvm: true
    tomcat_vg_name: vg_vroot
    tomcat_lv_name: lv_tomcat
    tomcat_lv_size: 10g

    tomcat_version: 8
    tomcat_datadir: "/var/lib/tomcat{{ tomcat_version }}"
    tomcat_conf_dir: "/etc/tomcat{{ tomcat_version }}"

    tomcat_java_memory: 128
    tomcat_user: "tomcat8"
    tomcat_group: "tomcat8"

    ### values could be 'mysql' or 'postgresql'
    tomcat_sql_connector: mysql

    #
    # variables in secret.yml
    #
    None yet.



Hosts example
------------

    [app_servers]
    jphtalend01l.btsys.local


Example Playbook
----------------

Playbook example:

    - name: Install Tomcat
      hosts: jphtalend01l.btsys.local
      vars:
        java_version: 8
        install_jdk: 0
        install_jre: 1
        tomcat_sql_connector: "mysql"
        tomcat_java_home: "/usr/lib/jvm/oracle-java8-jre-amd64"
      roles:
        - ansible-java
        - ansible-tomcat



Playbook launch
---------------

    ANSIBLE_HOST_KEY_CHECKING=False; ansible-playbook -i hosts playbook.yml --ask-pass --ask-become-pass --tags installation

Tags
----

- [installation] : Tomcat installation/configuration
- [rollback] : does nothing yet
- [testing] : Unit testing for Tomcat

License
-------

BSD

Author Information
------------------

BSO ISL
