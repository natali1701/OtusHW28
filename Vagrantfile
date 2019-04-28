# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "provisioning/playbook.yml"
    ansible.sudo = "true"
  end
  config.vm.provider "virtualbox" do |v|
          v.memory = 2048
  end
  config.vm.define "primary" do |primary|
    primary.vm.network "private_network", ip: "192.168.50.100", virtualbox__intnet: "private"
    primary.vm.hostname = "primary.otus.test"
  end
  config.vm.define "standby" do |standby|
    standby.vm.network "private_network", ip: "192.168.50.101", virtualbox__intnet: "private"
    standby.vm.hostname = "standby.otus.test"
  end
end
