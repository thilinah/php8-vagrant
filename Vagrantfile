Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  config.vm.network "private_network", ip: "192.168.10.100"
      config.vm.synced_folder ".", "/vagrant", type: "nfs"

      config.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = "2"
      end

      config.vm.provision "shell", inline: <<-SHELL
          sudo rm /etc/nginx/sites-enabled/default
          sudo ln -s /vagrant/deployment/nginx/sites-available/default /etc/nginx/sites-enabled/default

          sudo service nginx restart
          sudo chmod 755 -R /var/log
      SHELL
end