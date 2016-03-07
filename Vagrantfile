# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
 
  config.vm.box = "centos-6.5"

  config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"
  config.vm.network :forwarded_port, guest: 80, host: 8081
 
   config.vm.network "private_network", ip: "192.168.33.33"
   project_name = "site"
   config.vm.synced_folder "/newvagrant/site" , "/var/www/html/" + project_name + "/", :mount_options => ["dmode=777", "fmode=666"]

  #config.vm.synced_folder "../data", "/vagrant_data"
  config.omnibus.chef_version = :latest
  config.berkshelf.enabled = true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  config.vm.provision :chef_solo do |chef|
  chef.add_recipe "apache2"
  chef.add_recipe "php"
  chef.json = {
  :apache => {
  :Default_site_enabled => false
  }
 }
  
 end
end