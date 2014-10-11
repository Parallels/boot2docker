# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "boot2docker-builder"

  config.vm.box = "yungsang/coreos"

  config.vm.network :private_network, ip: "192.168.33.10"

  config.vm.synced_folder ".", "/home/core/vagrant", id: "core", type: "nfs", mount_options: ["nolock", "vers=3", "udp"]

  config.vm.provision :docker do |d|
    d.build_image "/home/core/vagrant/", args: "-t boot2docker"
    d.run "boot2docker", args: "--rm", cmd: "> /home/core/vagrant/boot2docker.iso",
      auto_assign_name: false, daemonize: false
  end
end
