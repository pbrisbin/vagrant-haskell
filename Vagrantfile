# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "lucid64"
  config.vm.box_url = "http://files.vagrantup.com/lucid64.box"

  sources = File.expand_path File.join(__FILE__, '..', '..')
  project = File.basename(sources)

  config.vm.customize [
    "modifyvm", :id,
    "--name",   "Haskell VM - #{project}",
    "--memory", "1024"
  ]

  config.ssh.forward_agent = true
  config.vm.share_folder("v-src", "/app", sources)

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe "apt"
    chef.add_recipe "haskell-platform"
    chef.add_recipe "heroku-toolbelt"
    chef.json.merge!({
      :ghc_version => '7.4.1',
      :haskell_platform_version => '2012.2.0.0'
    })
  end
end
