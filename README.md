# vagrant-zomboidserver
A quick and nasty vagrant provisioner to create a local virtual machine Project Zomboid server.

### What is it?

Everyone seems to complain at how hard it is to create a Linux based project zomboid server so I looked at how to facilitate the creation of one in the simplest way possible.

This simple script will pull a pre build ubuntu 15.04 server and install all the pre-requirements then install the PZ Dedicated server with no human interaction required from yourself other than to start the server when it's done.

## Requirements

To use this script you will need 2 bits of software installed : 

1) Virtualbox 

* https://www.virtualbox.org/wiki/Downloads
    
* This is the software that will run your virutal machine
    
    
2) Vagrant

* https://www.vagrantup.com/downloads.html
    
* This allows easy creation and management of virtual machines through the command line interface.
    
## How to use

If you know how to git then clone this repository or if you have no idea what I just said there just download the VagrantFile into an empty folder.

Open up a terminal window and chdir / cd to the folder with the Vagrant file and enter :

    vagrant up

The script will download the prebuilt ubuntu server, setup steam and Project Zomboid for you and tell you the ip address of the virtual machine on your local network.

You then need to acces the virtual machine by entering :

    vagrant ssh

You will then see a command prompt that looks like :

    vagrant@vagrant-ubuntu-vivid-64:~$
    
To start the server enter :

    cd cd Steam/steamapps/common/Project\ Zomboid\ Dedicated\ Server/
    
    ./start-server.sh

And that's it.  Connect your ProjectZomboid clients to your virtual machines local network IP address and profit!
  
