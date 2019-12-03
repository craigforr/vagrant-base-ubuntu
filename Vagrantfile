# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.provider "virtualbox"

  # Development Workstation -----------------------------------
  config.vm.define "workstation", primary: true do |workstation|
    # Ubuntu 18.04.2 LTS (Bionic Beaver)
    # https://app.vagrantup.com/ubuntu/boxes/bionic64
    # http://cloud-images.ubuntu.com/bionic/
    workstation.vm.box = "ubuntu/bionic64"
    workstation.vm.hostname = 'ubuntu1804lts'
    workstation.vm.network :private_network, ip: "192.168.56.20"
    workstation.vm.provider :virtualbox do |vb|
      vb.gui = false
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
      vb.customize ["modifyvm", :id, "--memory", 1024]
      vb.customize ["modifyvm", :id, "--name", "ubuntu1804lts"]
    end
  end
end
