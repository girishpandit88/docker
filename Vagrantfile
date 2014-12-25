# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'docker'
DOCKER_HOST_NAME = "dockerhost"
DOCKER_HOST_VAGRANTFILE = "./DockerHostVagrantfile"
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "dynamoDB" do |db|
    db.vm.provider "docker" do |d|
      d.build_dir = "./dynamoDB"
      d.name = "dynamoDB"
      d.remains_running = true
      d.has_ssh=false
      d.ports=["7777:7777"]
      d.vagrant_machine = "#{DOCKER_HOST_NAME}"
      d.vagrant_vagrantfile = "#{DOCKER_HOST_VAGRANTFILE}"
    end
  end
 
  config.vm.define "tomcat" do |t|
    t.vm.provider "docker" do |d|
      d.build_dir = "./tomcat"
      d.name = "tomcat"
      d.remains_running = true
      d.has_ssh=false
      d.ports=["8080:8080","8000:8000"]
      d.vagrant_machine = "#{DOCKER_HOST_NAME}"
      d.vagrant_vagrantfile = "#{DOCKER_HOST_VAGRANTFILE}"
    end
  end
 
  config.vm.define "memcached" do |m|
    m.vm.provider "docker" do |d|
      d.build_dir = "./memcached"
      d.name = "memcached"
      d.remains_running = true
      d.has_ssh=false
      d.ports=["11211:11211"]
      d.vagrant_machine = "#{DOCKER_HOST_NAME}"
      d.vagrant_vagrantfile = "#{DOCKER_HOST_VAGRANTFILE}"
    end
  end
end
