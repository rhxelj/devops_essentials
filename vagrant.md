#Vagrant site
https://www.vagrantup.com
there is a full description of how to configure and use vagrant in https://www.vagrantup.com/docs/

**basic configuration file**

vagrantfile

The first step in configuring any Vagrant project is to create a *vagrantfile*

    $ mkdir vagrant_directory
    $ cd vagrant_directory
    $ vagrant init         #this makes my vagrantfile

Next we create a box (is an image of a virtual machine)

    $ vagrant box add hashicorp/precise64     #where hashicorp/precise64 is the owner of the image and the image it self.
    
you can find more boxes in https://atlas.hashicorp.com/boxes/search

In order to use a box you need to configure you vagrantfile with the following

    Vagrant.configure("2") do |config|
      config.vm.box = "hashicorp/precise64"
    end

If you want to use an specific version of a box you can do it  by specifying config.vm.box_version for example:

```
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/precise64"
  config.vm.box_version = "1.1.0"
end
```
and iy you want to specify a URL to a box directly use config.vm.box_url:
```
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
end
```
Now we have to boot our Vagrant environment. Run the following from your terminal:

    $ vagrant up

now you can interact with the new amchine using SSH to ge into the machine:

    $ vagrant ssh

now you can interact with the machine and do whatever you want. but be careful about rm -rf /, becuase Vagrant shares a directory at /vagrant with the directory on the host containing your Vagrantfile.
To finish the session you can use CTRL+D.

    vagrant@precise64:~$ logout
    Connection to 127.0.0.1 closed.

When you finish your test you canrun vagrant destroy back on your host machine, and Vagrant will terminate the use of any resources by the virtual machine.

The vagrant destroy command does not actually remove the downloaded box file. To completely remove the box file, you can use the vagrant box remove command.


