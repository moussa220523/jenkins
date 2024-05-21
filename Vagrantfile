# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  disk_path = '/media/moussa/DiskMzss/VirtualBox VMs/ubuntu_bionic'
  config.vm.synced_folder ".", disk_path, type: "virtualbox"
  config.vm.box_check_update = false
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.define "docker" do |docker|
    docker.vm.box = "ubuntu/bionic64"
    disk_path = '/media/moussa/DiskMzss/VirtualBox VMs/docker'
    docker.vm.synced_folder ".", disk_path, type: "virtualbox"
    docker.vm.network "private_network", ip: "192.168.56.1"
    docker.vm.hostname = "docker"
    config.vm.network "forwarded_port", guest: 8080, host: 8888
    config.vm.network "forwarded_port", guest: 50000, host: 55555
    docker.vm.provision "shell", inline: <<-SHELL
      apt clean
      apt-get update
      apt-get remove docker docker-engine docker.io containerd runc -y
      apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common -y
      curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
      add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
      apt-get update -y
      apt-get install docker.io -y
    SHELL
  end

end
