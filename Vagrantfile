# -*- mode: ruby -*-
# vi: set ft=ruby :
 
Vagrant::Config.run do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"
  
  config.vm.forward_port 3000, 3000
  
  config.vm.share_folder "app", "/home/vagrant/app", "app/", :create => true

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks"]
    chef.add_recipe "apt"
    chef.add_recipe "build-essential"
    chef.add_recipe "rvm::vagrant"
    chef.add_recipe "rvm::system"

    chef.json.merge!({
      :rvm => {
        :default_ruby => 'ruby-1.9.3-p374'
      }
    })

    chef.add_recipe "git"
  end
end