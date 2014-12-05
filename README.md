Ansible Module HAProxy
===================

An Ansible module to handle state enabled/disabled server from haproxy using socket.
Showing the current and current weight for backend server(s) is default for both state, also it set weight for server(s) if 
provides while doing enable backend server(s).


Example
------

    # disable server in 'www' backend pool
    - haproxy: state=disabled host={{ inventory_hostname }} backend=www

    # disable server without backend pool name (apply to all available backend pool)
    - haproxy: state=disabled host={{ inventory_hostname }}

    # disable server, provide socket file
    - haproxy: state=disabled host={{ inventory_hostname }} socket=/var/run/haproxy.sock backend=www

    # disable backend server in 'www' backend pool and drop open sessions to it
    - haproxy: state=disabled host={{ inventory_hostname }} backend=www socket=/var/run/haproxy.sock shutdown_sessions=true

    # enable server in 'www' backend pool
    - haproxy: state=enabled host={{ inventory_hostname }} backend=www

    # enable server in 'www' backend pool with change server(s) weight
    - haproxy: state=enabled host={{ inventory_hostname }} socket=/var/run/haproxy.sock weight=10 backend=www

Dependencies
------------

Haproxy socket commands are restricted and can only be issued on sockets configured for level 'admin', 
Check - http://haproxy.1wt.eu/download/1.5/doc/configuration.txt,
Exampe: 'stats socket /var/run/haproxy.sock level admin'

License
-------

GPL

Author Information
------------------
Ravi Bhure <ravibhure@gmail.com>
