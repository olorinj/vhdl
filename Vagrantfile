# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
    config.vm.box = "bento/debian-11.2"
#    config.vm.network "forwarded_port", guest: 22, host: 2222
    config.vm.provider "virtualbox" do |vb|
      vb.name = "VHDL"
      vb.memory = 512
      vb.cpus = 1
      vb.customize ["modifyvm", :id, "--vram", "9"]
    end
    config.vm.provision "shell", inline: <<-SHELL
    sudo apt update
    sudo apt -y full-upgrade
    sudo apt -y install ghdl gtkwave pip python3
    sudo apt -y --purge autoremove
    pip install teroshdl
    mkdir $HOME/proyectos
    SHELL
    config.vm.synced_folder "proyectos/", "/home/vagrant/proyectos/"
  end