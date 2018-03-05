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

Um den DHCP Server zu installieren muss man zuerst das Paketverzeichnis aktualisieren. Im nächsten Schritt wird dann der DHCP Server installiert.

	sudo apt-get update
	sudo apt-get -y install isc-dhcp-server

***DHCP Konfiguration***

Das Vagrantfile im welchen sich die Konfigurationen des DHCP Servers befinden ist im Pfad /etc/dhcp/dhcpd.conf gespeichert. Im Konfigurationfile wird folgendes geändert:

- Domainname
- DNS
- DHCP Scope

Der Domainname lautet labor.local

	sudo sed -i 's/example.org/labor.local/g' /etc/dhcp/dhcpd.conf

Der DNS wurde auf 8.8.8.8 (Google DNS) konfiguriert.

	sudo sed -i 's/ns2.labor.local/8.8.8.8/g' /etc/dhcp/dhcpd.conf








