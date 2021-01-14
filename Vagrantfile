# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  
  config.vm.define "attacker" do |attacker|

    attacker.vm.box = "archlinux/archlinux"

    attacker.vm.network "private_network", ip: "10.0.2.9"

    attacker.vm.synced_folder "attacker", "/data"

    # Enable provisioning with a shell script. Additional provisioners such as
    # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
    # documentation for more information about their specific syntax and use.
    attacker.vm.provision "shell", inline: <<-SHELL
      sudo pacman -Sy --noconfirm bettercap nmap
    SHELL
  end

  config.vm.define "victim" do |victim|

    victim.vm.box = "moczalla/Windows10Edge"
    
    victim.vm.network "private_network", ip: "10.0.2.10"

  end

  config.vm.define "server" do |server|

    server.vm.box = "archlinux/archlinux"

    server.vm.network "private_network", ip: "10.0.2.11"

    server.vm.synced_folder "server", "/data"

    server.vm.provision "shell", inline: <<-SHELL
      sudo pacman -Sy --noconfirm nginx
      sudo cp /data/index.html /usr/share/nginx/html
      sudo systemctl start nginx
    SHELL
  end
end
