# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "lucid64"
  config.vm.box_url = "http://files.vagrantup.com/lucid64.box"

  config.vm.customize ["modifyvm", :id, "--name", "Haskell on Heroku", "--memory", "769"]

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe "haskell-platform"
    chef.add_recipe "heroku-toolbelt"
    chef.json.merge!({ :ghc_version => '7.0.4',
                       :haskell_platform_version => '2011.4.0.0'})
  end
end
