Ansible Module HAProxy
===================

An Ansible module to handle actions enable/disable server and set/get weight from haproxy using socket.



Example
------

    # disable server in 'www' backend
    - haproxy: action=disable_server host={{ inventory_hostname }} backend=www

    # disable server without backend name (apply to all backend)
    - haproxy: action=disable_server host={{ inventory_hostname }}

    # disable server, provide socket file
    - haproxy: action=disable_server host={{ inventory_hostname }} socket=/var/run/haproxy.sock backend=www

    # enable server in 'www' backend
    - haproxy: action=enable_server host={{ inventory_hostname }} backend=www

    # Change a server(s) weight
    - haproxy: action=set_weight host={{ inventory_hostname }} socket=/var/run/haproxy.sock weight=10 backend=www

    # Show the current weight and the initial weight of server(s)
    - haproxy: action=get_weight host={{ inventory_hostname }} socket=/var/run/haproxy.sock backend=www

Dependencies
------------

Haproxy socket commands are restricted and can only be issued on sockets configured for level 'admin', 
Check - http://haproxy.1wt.eu/download/1.4/doc/configuration.txt,
Exampe: 'stats socket /var/run/haproxy.sock level admin'

License
-------

GPL

Author Information
------------------
Ravi Bhure <ravibhure@gmail.com>
