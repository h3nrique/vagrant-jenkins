# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.define "node1" do |machine|
    machine.vm.network "forwarded_port", guest: 8080, host: 8080
    machine.vm.network "private_network", ip: "172.17.177.21"
  end

  config.vm.define 'controller' do |machine|
    machine.vm.network "private_network", ip: "172.17.177.11"

    machine.vm.provision :ansible_local do |ansible|
      ansible.playbook       = "playbook.yml"
      ansible.verbose        = true
      ansible.install        = true
      ansible.limit          = "all"
      ansible.inventory_path = "inventory"
    end
  end
end
