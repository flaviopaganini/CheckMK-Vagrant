# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.  
  config.vm.define "checkmk" do |checkmk|
    checkmk.vm.box = "ubuntu/xenial64"
    checkmk.vm.hostname = "server"
    checkmk.vm.network "private_network", ip:"192.168.55.101" 
		checkmk.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
		checkmk.vm.provider "virtualbox" do |vb|
	  vb.memory = "2048"  
	end  
	checkmk.vm.provision "shell", inline: <<-SHELL
		sudo apt-get update
		sudo wget https://mathias-kettner.de/support/Check_MK-pubkey.gpg
		sudo wget https://mathias-kettner.de/support/1.4.0p38/check-mk-raw-1.4.0p38_0.xenial_amd64.deb
		sudo apt-key add Check_MK-pubkey.gpg
		sudo apt-get -y install gdebi-core
		sudo gdebi -n check-mk-raw-1.4.0p38_0.xenial_amd64.deb
		sudo omd create TBZSide > login.txt
		sudo omd start TBZSide
		wget http://192.168.55.101/TBZSide/check_mk/agents/check-mk-agent_1.4.0p38-1_all.deb
		sudo gdebi -n check-mk-agent_1.4.0p38-1_all.deb
	SHELL
	end
	config.vm.define "client" do |client|
    client.vm.box = "ubuntu/xenial64"
    client.vm.hostname = "client"
    client.vm.network "private_network", ip:"192.168.55.100" 
	client.vm.provider "virtualbox" do |vb|
	  vb.memory = "512"  
	end 
	client.vm.provision "shell", inline: <<-SHELL
	sudo apt-get -y install gdebi-core
	sudo apt-get -y install xinetd
	wget http://192.168.55.101/TBZSide/check_mk/agents/check-mk-agent_1.4.0p38-1_all.deb
	sudo gdebi -n check-mk-agent_1.4.0p38-1_all.deb
SHELL
	end  
 end