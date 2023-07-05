Vagrant.configure("2") do |config|

  config.vm.define "ansible" do |ansible| 
    ansible.vm.box = "shekeriev/debian-11"
    ansible.vm.hostname = "controle"
    ansible.vm.network "public_network"
    ansible.vm.provider "virtualbox" do |vb|
      vb.name = "controle"
      vb.memory = "1024"
      vb.cpus = 2
    end
  end

  config.vm.define "web" do |web| 
    web.vm.box = "shekeriev/debian-11"
    web.vm.hostname = "aplicacao"
    web.vm.network "public_network"
    web.vm.provider "virtualbox" do |vb|
      vb.name = "aplicacao"
      vb.memory = "512"
      vb.cpus = 2
    end
  end

  config.vm.define "db" do |db| 
    db.vm.box = "shekeriev/debian-11"
    db.vm.hostname = "banco"
    db.vm.network "public_network"
    db.vm.provider "virtualbox" do |vb|
      vb.name = "banco"
      vb.memory = "1024"
      vb.cpus = 2
    end
  end
end




