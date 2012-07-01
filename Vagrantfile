# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "lucid32"
  config.vm.box_url = "http://files.vagrantup.com/lucid32.box"

  # Apache ports are accessible on localhost
  config.vm.forward_port 80, 8080
  config.vm.forward_port 443, 8443


  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks"]

    chef.data_bags_path = ["data_bags"]

    chef.add_recipe "postgresql::server"
    chef.add_recipe "chiliproject"
    chef.add_recipe "chiliproject::apache2"

    chef.log_level = :debug
  end
end
