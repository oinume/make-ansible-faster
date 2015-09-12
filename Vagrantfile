# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant::configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "ubuntu-14.04"
  config.vm.network :private_network, ip: "192.168.99.100"

  # VM option
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", 1024]
    v.customize ["modifyvm", :id, "--cpus", 1]
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--nictype1", "virtio"]
    v.customize ["modifyvm", :id, "--nictype2", "virtio"]
  end

  # Ansible
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.verbose = "v"
  end

  # vagrant plugin install vagrant-cachier
  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :box
  end
end
