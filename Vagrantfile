# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.

  config.vm.box = "ubuntu/vivid64"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  config.vm.network "public_network"

  config.vm.provider "virtualbox" do |vb|
     vb.gui = false
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
    # Set the number of cores for the VM   
    vb.cpus = "2"
    vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
  end

  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get upgrade -y
    apt-get install default-jdk screen lib32gcc1 -y
    mkdir steamcmd
    cd steamcmd
    wget http://media.steampowered.com/installer/steamcmd_linux.tar.gz
    tar -xvzf steamcmd_linux.tar.gz
    ./steamcmd.sh +login anonymous +app_update 380870 -validate +exit
    mv /root/Steam /home/vagrant
    chown vagrant:vagrant /home/vagrant -R
    echo '#################################'
    echo ''
    echo ' Make a note of the IP address!!'
    echo ''
    ifconfig  | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'
  SHELL
end
