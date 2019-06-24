# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  VAGRANT_VM_PROVIDER = "virtualbox"
  machine_box = "centos/7"

  config.vm.define "workshop1" do |machine|
    machine.vm.box = machine_box
    machine.vm.hostname = "workshop1"
    machine.vm.network "private_network", ip: "192.168.44.11"
    machine.vm.provision :shell, :inline => "sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config; sudo systemctl restart sshd;", run: "always"
    machine.vm.provider "virtualbox" do |node|
        node.name = "workshop1"
        node.memory = 2048
        node.cpus = 1
    end
   end
end
