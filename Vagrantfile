# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/precise64"
  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
  end
  
  config.vm.define "server1" do |server1|
    server1.vm.hostname = "server1"
    server1.vm.network "private_network", ip: "192.168.0.10"
	server1.vm.provision "shell", inline: <<-SHELL
	  echo '192.168.0.11 server2.local' >> /etc/hosts
	SHELL
  end
  
  config.vm.define "server2" do |server2|
    server2.vm.hostname = "server2"
    server2.vm.network "private_network", ip: "192.168.0.11"
	server2.vm.provision "shell", inline: <<-SHELL
      apt-get install git -y 
	  git clone git://github.com/vitali-shautsou/EPAM-Training-Module-2
	  cd EPAM-Training-Module-2/
	  git checkout origin/task2
	  cat test.txt
	  echo '192.168.0.10 server1.local' >> /etc/hosts
    SHELL
  end
end
