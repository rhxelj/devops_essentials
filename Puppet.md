Puppet is used to manage IT infrastructure.
we have **Puppet master** that contain **manifest** (files with instructions) for all clients (puppet slaves or agents)


**Installation**

Debian, Ubuntu
Available by default

    apt-get install puppet       # On clients (nodes)
    apt-get install puppetmaster # On server (master)
RedHat, Centos, Fedora
Add EPEL repository or RHN Extra channel

    yum install puppet        # On clients (nodes)
    yum install puppet-server # On server (master)
