# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define "attacker" do |attacker|

    attacker.vm.box = "archlinux/archlinux"

    attacker.vm.hostname = "attacker"

    attacker.vm.synced_folder "attacker", "/data"

    attacker.vm.provider :virtualbox do |vb|
      vb.name = "mitm_attacker"
    end

    attacker.vm.provision "shell", inline: <<-SHELL
      pacman -Sy --noconfirm bettercap nmap
    SHELL
  end

  config.vm.define "victim" do |victim|

    victim.vm.box = "xnohat/windows10lite"

    victim.vm.hostname = "victim"

    victim.vm.guest = :windows

    victim.vm.communicator = "winrm"

    victim.vm.provider :virtualbox do |vb|
      vb.name = "mitm_victim"
    end
    
  end

  config.vm.define "server" do |server|

    server.vm.box = "archlinux/archlinux"

    server.vm.hostname = "server"

    server.vm.synced_folder "server", "/data"
    
    server.vm.provider :virtualbox do |vb|
      vb.name = "mitm_server"
    end

    server.vm.provision "shell", inline: <<-SHELL
      sudo pacman -Sy --noconfirm nginx
      sudo cp /data/index.html /usr/share/nginx/html
      sudo systemctl start nginx
    SHELL
  end
end
