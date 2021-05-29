# Defines our Vagrant environment
#
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # create mgmt node
  config.vm.define :mgmt do |mgmt_config|
      mgmt_config.vm.box = "ubuntu/trusty64"
      mgmt_config.vm.hostname = "mgmt"
      mgmt_config.vm.network :private_network, ip: "10.0.15.30"
      mgmt_config.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
      end
      mgmt_config.vm.provision :shell, path: "bootstrap-mgmt.sh"
  end

  # create load balancer
  config.vm.define :sftpserver do |sftpserver_config|
      sftpserver_config.vm.box = "ubuntu/trusty64"
      sftpserver_config.vm.hostname = "sftpserver"
      sftpserver_config.vm.network :private_network, ip: "10.0.15.31"
      sftpserver_config.vm.network "forwarded_port", guest: 80, host: 8080
      sftpserver_config.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
      end
  end
end
