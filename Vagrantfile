# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'getoptlong'

opts = GetoptLong.new(
        [ '--help', '-h', GetoptLong::NO_ARGUMENT ],
        [ '--java', GetoptLong::OPTIONAL_ARGUMENT ],
        [ '--box', GetoptLong::OPTIONAL_ARGUMENT ],
        [ '--memory', GetoptLong::OPTIONAL_ARGUMENT ],
)

#Defaults
box = 'precise64' #Vagrant box name
java = 'openjdk-7-jre' #java pkg name
memory = 1024 #VM RAM

#Parse opts
opts.each do |opt, arg|
    case opt
         when '--java'
             java = arg
         when '--memory'
             memory = arg
         when '--box'
             box = arg
         when '--help'
             puts <<-EOF
vagrant [vagrant_options] [extra_options]

-h, --help:
  show help

--java:
  specify java package (default: openjdk-7-jre): openjdk-6-jre, openjdk-7-jre

--memory:
  specify VM memory in MB (default: 1024)

--box:
  specify Vagrant base box (default:precise64): precise32, precise64

        EOF
    end
end

puts "Configuration:"
puts "box #{box}"
puts "java #{java}"
puts "memory #{memory}"
puts ""

#(Based on Vagrantfile generated via "vagrant init")
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  #config.vm.box = "precise64"
  config.vm.box = box

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  #config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.box_url = "http://files.vagrantup.com/" + box + ".box"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
     vb.memory = memory
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
  SHELL
  # Provision Java
  config.vm.provision "shell", inline: "sudo apt-get install -y " + java

end
