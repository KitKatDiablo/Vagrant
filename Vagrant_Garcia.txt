Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
  config.vm.synced_folder ".", "/var/www/html"  
 config.vm.provider "virtualbox" do |vb|
  vb.memory = "2024"  
 end
  config.vm.provision "shell", inline: <<-SHELL 
    sudo apt-get update
    sudo apt-get -y install apache2
    sudo apt-get install mysql-server mysql-client

  SHELL
end