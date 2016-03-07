# HHVM Vagrant Box

### The source environment used for my vagrant box on Atlas, server4001/ubuntu-hhvm.

#### NOTE: This is the environment used to build the Vagrant box. If you are looking for an HHVM environment, just use the box: [server4001/ubuntu-hhvm](https://atlas.hashicorp.com/server4001/boxes/ubuntu-hhvm).

Comes with:

* Ubuntu 12.04
* HHVM v3.12.0 (rel)
* Nginx v1.8.1
* MySQL v5.5.47
* Beanstalkd v1.4.6
* Redis v2.2.12
* Memcached v1.4.13

Also has a Vim plugin for writing Hack code.

### Packaging the box:

* `vagrant up`
* Make any changes you need to the box. Be sure to reflect these changes in the provisioning script.
* Before packaging up the box, ssh in, and run the commands that are at the end of `Vagrantfile`.
* Package up the box with `vagrant package --output server4001-hhvm-0.2.1.box`. Replace `0.2.1` with the version number.
* Destroy the vm with `vagrant destroy -f`.
* Add the new box to vagrant's local list with: `vagrant box add server4001/hhvm-021 server4001-hhvm-0.2.1.box`. Again, replace `021` and `0.2.1` with the version number.
* Delete the `.vagrant` folder with `rm -rf .vagrant`.
* Test out the box by going to a different folder, running `vagrant init server4001/hhvm-021`, and changing the `Vagrantfile` to fit your needs. Next, run `vagrant up`, and ensure everything is working.
* Create a new version on Atlas.
* Add a new provider to the version. The type should be `virtualbox`. Upload the box file.

### Todos:

* Switch HHVM from using a port to using a socket.
