# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "almalinux/9"
  config.vm.box_version = "9.2.20230513"

  # config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
    dnf install -y docker-ce
    usermod -aG docker vagrant
    systemctl enable docker --now
  SHELL
end
