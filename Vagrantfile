# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

  # If true, agent forwarding over SSH connections is enabled. Defaults to false.
  config.ssh.forward_agent = true

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provision "shell", inline: <<PROVISIONSCRIPT
  apt-get update
  apt-get install -y php5-common php5-cli php5-fpm nginx

  php -r "readfile('https://getcomposer.org/installer');" | php
  mv composer.phar /usr/local/bin/composer
PROVISIONSCRIPT

  config.vm.provision "file", source: "provisioning/nginx-sites/default", destination: "/tmp/nginx-default-site"

  config.vm.provision "shell", inline: <<PROVISIONSCRIPT
  mv /tmp/nginx-default-site /etc/nginx/sites-enabled/default
  service nginx restart
PROVISIONSCRIPT

  config.vm.hostname = '99-simplest-silex'
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
end
