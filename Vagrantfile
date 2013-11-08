# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'json'

host_cache_path = File.expand_path("../.cache", __FILE__)
guest_cache_path = "/tmp/vagrant-cache"

# ensure the cache path exists
FileUtils.mkdir(host_cache_path) unless File.exist?(host_cache_path)

Vagrant.configure("2") do |config|

  config.vm.define :chef_server do |chef_config|
    chef_config.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--cpus", 2]
      vb.customize ["modifyvm", :id, "--memory", 1024]
    end

    chef_config.vm.box = "precise64"
    chef_config.vm.network :private_network, ip: "10.33.33.33"
    chef_config.vm.synced_folder host_cache_path, guest_cache_path

    VAGRANT_JSON = JSON.parse(Pathname(__FILE__).dirname.join('nodes', 'vagrant.json').read)

    chef_config.vm.provision :chef_solo do |chef|
       chef.cookbooks_path = ["site-cookbooks", "cookbooks"]
       chef.roles_path = "roles"
       chef.data_bags_path = "data_bags"
       chef.provisioning_path = guest_cache_path

       chef.run_list = VAGRANT_JSON.delete('run_list') if VAGRANT_JSON['run_list']

       chef.json = VAGRANT_JSON
    end
  end

  config.vm.define :chef_client do |chef_client_config|
    chef_client_config.vm.box = "precise64"
    chef_client_config.vm.network :private_network, ip: "10.33.33.50"
  end
end
