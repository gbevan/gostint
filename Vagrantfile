# -*- mode: ruby -*-
# vi: set ft=ruby :

extras = "~vagrant/go/src/github.com/gbevan/goswim/scripts/init_main.sh"

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "ubuntu-dev", primary: true do |ubuntu|
    ubuntu.vm.provision "shell", inline: extras
    ubuntu.vm.synced_folder "~/go", "/home/vagrant/go"
    ubuntu.vm.provider "docker" do |d|
      d.image = "gbevan/vagrant-ubuntu-dev:bionic"
      d.has_ssh = true
      d.ports = ["3232:3232", "8300:8200"]
      d.privileged = true # needed for dind
    end
  end
end
