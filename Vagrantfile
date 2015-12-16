# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
  end
  config.vm.network "forwarded_port", guest: 8000, host:8000, auto_correct: true
  config.vm.network "forwarded_port", guest: 8080, host:8080, auto_correct: true
  config.vm.network "forwarded_port", guest: 11211, host:11211, auto_correct: true
  config.vm.network "forwarded_port", guest: 7777, host:7777, auto_correct: true
  config.vm.provision :docker
  config.vm.provision :docker_compose, yml: "/vagrant/docker-compose.yml", run: "always"
end
