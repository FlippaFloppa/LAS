# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
	config.vm.box = "debian/bullseye64"
	
	config.vm.provider "virtualbox" do |vb|
		vb.linked_clone=true
	end
	
	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "ansible_playbook.yml"
  	end

	config.vm.define "router" do |machine|
		machine.vm.hostname = "router"
		machine.vm.network "private_network", virtualbox__intnet: "LAN1", auto_config: false
		machine.vm.network "private_network", virtualbox__intnet: "LAN2", auto_config: false	
	end
	config.vm.define "servermain" do |machine|
		machine.vm.hostname = "servermain"
		machine.vm.network "private_network", virtualbox__intnet: "LAN2", auto_config: false, mac: "08002709A501"
	end
	config.vm.define "server" do |machine|
		machine.vm.hostname = "server"
		machine.vm.network "private_network", virtualbox__intnet: "LAN2", auto_config: false
	end
	config.vm.define "server2" do |machine|
		machine.vm.hostname = "server2"
		machine.vm.network "private_network", virtualbox__intnet: "LAN2", auto_config: false
	end

	config.vm.define "client1" do |machine|
		machine.vm.hostname = "client1"
		machine.vm.network "private_network", virtualbox__intnet: "LAN1", auto_config: false
	end
	config.vm.define "client" do |machine|
		machine.vm.hostname = "client"
		machine.vm.network "private_network", virtualbox__intnet: "LAN1", auto_config: false
	end	
end
