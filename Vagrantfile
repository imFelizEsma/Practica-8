Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/bionic64" 
  
    config.vm.network "private_network", ip: "192.168.56.10"
  
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    config.vm.synced_folder "./html", "/var/www/html"
  
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
      sudo chown -R www-data:www-data /var/www/html
      sudo chmod -R 755 /var/www/html
    SHELL
  end
  