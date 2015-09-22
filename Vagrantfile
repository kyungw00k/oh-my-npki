# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "kyungw00k/windows-10-pro-kn-x64"

  # Port Forward 설정
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # 기본 Mount 폴더 제거
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # 공인인증서 위치 Mount
  config.vm.synced_folder "./NPKI", "/Users/vagrant/AppData/LocalLow/NPKI"

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

  # XX 은행
  #config.vm.provision :shell, :name => "XX 은행 통합 설치 파일 설치", :path => "bootstrap/XXX.exe /quiet", :privileged => true
end
