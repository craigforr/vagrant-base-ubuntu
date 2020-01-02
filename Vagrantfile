# -*- mode: ruby -*-
# vi: set ft=ruby :

UBUNTU_COUNT = 1

Vagrant.configure("2") do |config|

  config.vm.provider "virtualbox"

  if UBUNTU_COUNT > 0 then
    (1..UBUNTU_COUNT).each do |i|
      hostname = "ubuntu%02d" % i
      config.vm.define hostname do |ubuntu|
        # Ubuntu 18.04.2 LTS (Bionic Beaver)
        # https://app.vagrantup.com/ubuntu/boxes/bionic64
        # http://cloud-images.ubuntu.com/bionic/
        ubuntu.vm.box = "ubuntu/bionic64"
        ubuntu.vm.hostname = hostname
        ubuntu.vm.network :private_network, ip: "192.168.56.#{i + 30}"
        ubuntu.vm.synced_folder ".vagrant_shared", "/home/vagrant/shared", disabled: true
        ubuntu.vm.provider :virtualbox do |v|
          v.gui = false
          v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
          v.customize ["modifyvm", :id, "--memory", 512]
          v.customize ["modifyvm", :id, "--name", hostname]
        end
        ubuntu.vm.provision "shell", inline: "echo \"IPs: $(hostname -I)\"", keep_color: true
      end
    end
  end

end
