# Simplest-Silex-Application-Possible
Simplest Silex application possible, with a vagrant box to run it for demo code.

## Dependencies

The following software needs to be installed
* [Vagrant](www.vagrantup.com)
* [Virtual Box](www.virtualbox.org)
* [Vagrant Hosts Manager Plugin](https://github.com/smdahlen/vagrant-hostmanager)

## Setup
Start the VM
```
vagrant up
```
Login to the VM
```
vagrant ssh
```
When on the VM install [Silex](silex.sensiolabs.org) and it's dependencies
```
cd /vagrant
composer install
```
Then hit the endpoint, from the your host machine, or the guest VM.
```
wget -O- http://99-simplest-silex/hello/world
```
