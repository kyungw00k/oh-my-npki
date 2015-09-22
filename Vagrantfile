# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "kyungw00k/windows-10-pro-kn-x64"

  # config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder "./NPKI", "/Users/vagrant/AppData/LocalLow/NPKI"

  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
end
