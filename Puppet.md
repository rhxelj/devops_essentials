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

**Configuration Files for Puppet Master**

>/etc/puppet/puppet.conf

I add two lines here 
>dns_alt_names = puppet,puppet.mydomain.com  #here I put the name and alias of my puppet server
>certname = puppet

now I generate the certificate from the master node
    
    $sudo -u puppet puppet master --no-daemonize --verbose
    
you can CTRL-C to return to terminal
now start and enable the services

    #systemctl start puppetmaster
    #systemctl enable puppetmaster
    
now I go to the client and I install puppet agent 

now I can configure the puppet agent 

    #vi /etc/puppet/puppet.conf
    
I make changes in the agent part of the configuration
>server = puppet.mydomain.com # the nane I define in /etc/puppet/puppet.conf in my server
now I need to generate the certificate to connect to my puppet master
    #puppet agent -t 
Now I return to my puppet master and I run 
    #puppet cert list
It will show me a list of certificates to sign in. in order to add the m to my 
puppet master I run this command
    #puppet cert sing name #where name is the name that appears in "" in the lprevious command
    
Now I return to my agent node and start the proper services
    #systemctl start puppet
    #systemctl enable puppet

to know if the master and the agent are conected I can run a fingerpritn verification
    #puppet agent --fingerprint
and what I have to do is compare de result with the one when I sign in the cert key in the puppet master
 
know I can configure manifest files.



