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

  # 신한은행
  config.vm.provision :shell, :name => "[신한은행] 개인 방화벽(AOS)", :inline => "/bootstrap/shinhan/InstAosmgr.exe", :args => "/S", :privileged => true
  config.vm.provision :shell, :name => "[신한은행] 공인인증 / 보안통신(INISAFE Web)", :inline => "/bootstrap/shinhan/INIS70.exe", :args => "/S", :privileged => true
  #config.vm.provision :shell, :name => "[신한은행] 키보드 보안(Secure Keystroke)", :inline => "/bootstrap/shinhan/SCSKInstTotal.exe", :args => "/S", :privileged => true

  # 국민은행
  config.vm.provision :shell, :name => "[국민은행] 공인인증서 보안", :inline => "/bootstrap/kbstar/delfino.exe", :args => "/SILENT", :privileged => true
  #config.vm.provision :shell, :name => "[국민은행] 개인PC 방화벽(nProtect-Netizen)", :inline => "/bootstrap/kbstar/IE_nProtect_Netizen.exe", :args => "/S", :privileged => true
  #config.vm.provision :shell, :name => "[국민은행] 로그수집기(nProtect-SecuLog)", :inline => "/bootstrap/kbstar/npEfdsWCtrlSetup.exe", :args => "/S", :privileged => true

end
