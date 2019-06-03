Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
  config.vm.synced_folder ".", "/var/www/html"  
config.vm.provider "virtualbox" do |vb|
  vb.memory = "2048"
end
#Hier wird die VM konfiguriert
config.vm.provision "shell", inline: <<-SHELL
#Installation von apache2 
  sudo apt-get update
  sudo apt-get -y install apache2 
  
#fw installation und regeln bestimmen port 80 und 22 geöffnet  
  sudo apt-get install ufw
  sudo ufw allow 80/tcp
  sudo ufw allow 22/tcp
  sudo ufw allow out 22/tcp 
  sudo ufw enable
  
#ssh inatllation 
  sudo apt-get -y install openssh-server
  
#installation der module für den Reverse proxy  
  sudo apt-get -y install libapache2-mod-proxy-html
  sudo apt-get -y install libxml2-dev

#module in apache aktivieren  
  sudo a2enmod proxy
  sudo a2enmod proxy_html
  sudo a2enmod proxy_http

  sudo service apache2 restart
#neue gruppe erstellen mit 2Benutzern und Passwort setzen  
  sudo groupadd admin
      sudo useradd user01 -g admin -m -s /bin/bash 
      sudo useradd user02 -g admin -m -s /bin/bash 
      sudo chpasswd <<<user01:1234	
      sudo chpasswd <<<user02:1234
  exit
SHELL
end