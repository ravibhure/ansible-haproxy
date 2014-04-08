Ansible Module HAProxy
===================

An Ansible module to handle enable/disable server from haproxy.



Example
------

    # disable backend server in 'www' frontend
    - haproxy: action=disable_server host={{ inventory_hostname }} frontend=www

    # disable backend server without frontend name (applied to all)
    - haproxy: action=disable_server host={{ inventory_hostname }}

    # disable server, provide socket file
    - haproxy: action=disable_server host={{ inventory_hostname }} socket=/var/run/haproxy.sock frontend=www

    # enable backend server in 'www' frontend
    - haproxy: action=enable_server host={{ inventory_hostname }} frontend=www


Dependencies
------------

enable or disable commands are restricted and can only be issued on sockets configured for level 'admin', 
Check - http://haproxy.1wt.eu/download/1.4/doc/configuration.txt,
Exampe: 'stats socket /var/run/haproxy.sock level admin'

License
-------

GPL

Author Information
------------------
Ravi Bhure <ravibhure@gmail.com>
