# Vagrant
Vagrant Modul300

***Vm Konfiguration***

Zu Beginn habe ich die Multi VM Umgebung aufgebaut und habe mit verschiedenen Vagrantfiles Server aufgesetzt.

Für die VM auf der wir den DHCP Server installieren wollen, habe ich mich für Debian entschieden.
Dieser wurde folgendermassen konfiguriert

- IP: 192.168.10.5
- Hostname: dhcp
- RAM: 2024 MB
- VM Box: Debian Vagrant Box

Bei Vagrant kann auch ausgewählt werden, mit welchem Tool man die VM aufsetzten möchte. Wir wählen dazu Virtualbox.


	Vagrant.configure(2) do |config|  

 	 config.vm.define "dhcp" do |dhcp|
  
  	  dhcp.vm.box = "debian/jessie64"
    
   	 dhcp.vm.hostname = "dhcp"	
    
  	  dhcp.vm.network "private_network", ip:"192.168.50.4" 
    
	dhcp.vm.provider "virtualbox" do |vb|	
	
	vb.memory = "1024"	
