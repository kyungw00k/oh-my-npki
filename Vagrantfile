# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "kyungw00k/windows-7-pro-k-x64"

  # Port Forward 설정
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # 기본 Mount 폴더 제거
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # 공인인증서 위치 Mount
  config.vm.synced_folder "./NPKI", "/Users/vagrant/AppData/LocalLow/NPKI"

  # 은행 관련 설치 파일 위치
  config.vm.synced_folder "./bootstrap", "/bootstrap"

  # See http://www.virtualbox.org/manual/ch08.html
  config.vm.provider "virtualbox" do |vb|
    # GUI Mode
    vb.gui = true

    # RAM
    vb.memory = "2048"

    # Audio
    vb.customize ["modifyvm", :id, "--audio", "coreaudio", "--audiocontroller", "hda"]

    # USB 2.0
    vb.customize ["modifyvm", :id, "--usb", "on", "--usbehci", "on"]

    # Video RAM
    vb.customize ["modifyvm", :id, "--vram", "128"]

    # Video Accelation
    vb.customize ["modifyvm", :id, "--accelerate3d", "on", "--accelerate2dvideo", "on"]

    # Clipboard
    vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]

    # Drag & Drop
    vb.customize ["modifyvm", :id, "--draganddrop", "bidirectional"]

    # Optical Drive
    vb.customize ["storageattach", :id, "--storagectl", "IDE Controller", "--port", "0", "--device", "1", "--type", "dvddrive", "--medium", "emptydrive"]
  end

  #
  config.vm.provision :shell, :inline => "/bootstrap/init.ps1", :privileged => true
end
