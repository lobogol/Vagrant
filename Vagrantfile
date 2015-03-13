Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/precise32"
  config.vm.provider "virtualbox" do |v|
    v.gui = false
    v.memory = 512
    v.cpus = 1
  end

    config.vm.define :db do |db_config|
      db_config.vm.base_mac = "080027668CDB"
      db_config.vm.host_name = "db"
      db_config.vm.network "private_network", ip: "192.168.33.30"
      db_config.vm.network "forwarded_port", guest: 80, host: 8090
      #chef_config.vm.synced_folder "../data", "/vagrant_data"
    config.vm.provider "virtualbox" do |db|
        db.gui = false
        db.name = "db"
        db.memory = 512
        db.cpus = 1
    end
  end

    config.vm.define :web do |web_config|
      web_config.vm.base_mac = "080027668CAD"
      web_config.vm.host_name = "web"
      web_config.vm.network "private_network", ip: "192.168.33.20"
      web_config.vm.network "forwarded_port", guest: 80, host: 8091
      #web_config.vm.synced_folder "../data", "/vagrant_data"
    config.vm.provider "virtualbox" do |web|
        web.gui = false
        web.name = "web"
        web.memory = 512
        web.cpus = 1
     end
  end

    config.vm.define :chef do |chef_config|
      chef_config.vm.host_name = "chef"
      chef_config.vm.network "private_network", ip: "192.168.33.10"
      chef_config.vm.network "forwarded_port", guest: 80, host: 8080
      #chef_config.vm.synced_folder "../data", "/vagrant_data"
    config.vm.provider "virtualbox" do |chef|
        chef.gui = false
        chef.name = "chef"
        chef.memory = 512
        chef.cpus = 1
    end
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y mc htop git
    SHELL
end
