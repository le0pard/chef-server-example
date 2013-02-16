# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'rubygems'
require 'bundler'

Bundler.require
require 'multi_json'
require 'berkshelf/vagrant'

host_cache_path = File.expand_path("../.cache", __FILE__)
guest_cache_path = "/tmp/vagrant-cache"

# ensure the cache path exists
FileUtils.mkdir(host_cache_path) unless File.exist?(host_cache_path)

Vagrant::Config.run do |config|

  config.vm.define :chef do |chef_config|
    config.vm.customize ["modifyvm", :id, "--cpus", 2]
    config.vm.customize ["modifyvm", :id, "--memory", 1024]
  
    chef_config.vm.box = "precise64"
    chef_config.vm.network :hostonly, "10.33.33.33"
    chef_config.vm.share_folder "cache", guest_cache_path, host_cache_path

    chef_config.ssh.max_tries = 40
    chef_config.ssh.timeout   = 120
      
    chef_config.berkshelf.berksfile_path = Pathname(__FILE__).dirname.join('Berksfile')
    
    VAGRANT_JSON = MultiJson.load(Pathname(__FILE__).dirname.join('nodes', 'vagrant.json').read)

    chef_config.vm.provision :chef_solo do |chef|
       chef.cookbooks_path = ["site-cookbooks", "cookbooks"]
       chef.roles_path = "roles"
       chef.data_bags_path = "data_bags"
       chef.provisioning_path = guest_cache_path

       chef.json = VAGRANT_JSON
       VAGRANT_JSON['run_list'].each do |recipe|
        chef.add_recipe(recipe)
       end if VAGRANT_JSON['run_list']

       Dir["#{Pathname(__FILE__).dirname.join('roles')}/*.json"].each do |role|
         chef.add_role(role)
       end
    end
  end
  
  config.vm.define :chef_client do |chef_client_config|
    chef_client_config.vm.box = "precise64"
    chef_client_config.vm.network :hostonly, "10.33.33.50"
    
    chef_client_config.ssh.max_tries = 40
    chef_client_config.ssh.timeout   = 120
  end
end
