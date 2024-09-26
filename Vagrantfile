# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox"

  config.vm.define "revproxy" do |proxy| 
    proxy.vm.box = "debian/bullseye64"
    proxy.vm.network "forwarded_port", guest:80, host:8080
    proxy.vm.network "private_network", ip:"192.168.57.10"
    proxy.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y nginx
  SHELL
  end #proxy

  config.vm.define "database" do |db|
    db.vm.box =  "rockylinux/9"
    db.vm.network "private_network", ip:"192.168.57.11"
    db.vm.provision "shell", inline: <<-SHELL
    dnf check-update
    dnf -y install mariadb
    SHELL
  end #db

  config.vm.define "app" do |app|
    app.vm.box = "ubuntu/focal64"
    app.vm.network "private_network", ip:"192.168.57.13"
    app.vm.provision "shell", inline: <<-SHELL
    apt update
    apt -y install python3
    apt -y install python3-pip
    pip install -U flask
    SHELL
  end #app

end
