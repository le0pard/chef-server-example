http://docs.opscode.com/breaking_changes_chef_11.html

bundle

knife solo init .

http://berkshelf.com/

berks install



https://github.com/opscode/omnibus-chef/blob/master/files/chef-server-cookbooks/chef-server/attributes/default.rb


net-http-persistent-2.8/lib/net/http/persistent/ssl_reuse.rb:70:in `connect': SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed (Faraday::Error::ConnectionFailed)



vagrant up
/Users/leo/.rvm/gems/ruby-1.9.3-p385/gems/hashie-2.0.0/lib/hashie/mash.rb:80: warning: redefining `object_id' may cause serious problems
[chef] Importing base box 'precise64'...
[chef] The guest additions on this VM do not match the install version of
VirtualBox! This may cause things such as forwarded ports, shared
folders, and more to not work properly. If any of those things fail on
this machine, please update the guest additions and repackage the
box.

Guest Additions Version: 4.1.18
VirtualBox Version: 4.2.6
[chef] Matching MAC address for NAT networking...
[chef] Clearing any previously set forwarded ports...
[chef] Forwarding ports...
[chef] -- 22 => 2200 (adapter 1)
[Berkshelf] installing cookbooks...
[Berkshelf] Installing chef-server (2.0.0) from git: 'git://github.com/opscode-cookbooks/chef-server.git' with branch: 'a3b94e30b599f901eee2eb1af5bc1f4ef011cae4'
[chef] Creating shared folders metadata...
[chef] Clearing any previously set network interfaces...
[chef] Booting VM...
[chef] Waiting for VM to boot. This can take a few minutes.
[chef] VM booted and ready for use!
[chef] Mounting shared folders...
[chef] -- v-root: /vagrant
[chef] -- v-csr-4: /tmp/vagrant-chef/chef-solo-4/roles
[chef] -- v-csc-3: /tmp/vagrant-chef/chef-solo-3/cookbooks
[chef] -- v-csc-2: /tmp/vagrant-chef/chef-solo-2/cookbooks
[chef] -- v-csc-1: /tmp/vagrant-chef/chef-solo-1/cookbooks
[chef] -- v-csdb-5: /tmp/vagrant-chef/chef-solo-5/data_bags
[chef] Running provisioner: Vagrant::Provisioners::ChefSolo...
[chef] Generating chef JSON and uploading...
[chef] Running chef-solo...
stdin: is not a tty
[Sat, 16 Feb 2013 12:09:03 +0000] INFO: *** Chef 0.10.10 ***
[Sat, 16 Feb 2013 12:09:03 +0000] INFO: Setting the run_list to ["role[chef]"] from JSON
[Sat, 16 Feb 2013 12:09:03 +0000] INFO: Run List is [role[chef]]
[Sat, 16 Feb 2013 12:09:03 +0000] INFO: Run List expands to [chef-server::default]
[Sat, 16 Feb 2013 12:09:03 +0000] INFO: Starting Chef Run for precise64
[Sat, 16 Feb 2013 12:09:03 +0000] INFO: Running start handlers
[Sat, 16 Feb 2013 12:09:03 +0000] INFO: Start handlers complete.
[Sat, 16 Feb 2013 12:09:03 +0000] INFO: Omnitruck download-server request: http://www.opscode.com/chef/download-server?p=ubuntu&pv=12.04&m=x86_64&v=latest&prerelease=false&nightlies=false
[Sat, 16 Feb 2013 12:09:04 +0000] INFO: Downloading chef-server package from: http://opscode-omnitruck-release.s3.amazonaws.com/ubuntu/12.04/x86_64/chef-server_11.0.6-1.ubuntu.12.04_amd64.deb
[Sat, 16 Feb 2013 12:09:04 +0000] INFO: Processing remote_file[/tmp/vagrant-chef/chef-server_11.0.6-1.ubuntu.12.04_amd64.deb] action create (chef-server::default line 40)
[Sat, 16 Feb 2013 12:15:34 +0000] INFO: remote_file[/tmp/vagrant-chef/chef-server_11.0.6-1.ubuntu.12.04_amd64.deb] updated
[Sat, 16 Feb 2013 12:15:34 +0000] INFO: Processing package[chef-server_11.0.6-1.ubuntu.12.04_amd64.deb] action install (chef-server::default line 51)
[Sat, 16 Feb 2013 12:16:05 +0000] INFO: package[chef-server_11.0.6-1.ubuntu.12.04_amd64.deb] installed version 11.0.6-1.ubuntu.12.04
[Sat, 16 Feb 2013 12:16:05 +0000] INFO: Processing directory[/etc/chef-server] action create (chef-server::default line 63)
[Sat, 16 Feb 2013 12:16:05 +0000] INFO: directory[/etc/chef-server] created directory /etc/chef-server
[Sat, 16 Feb 2013 12:16:05 +0000] INFO: Processing template[/etc/chef-server/chef-server.rb] action create (chef-server::default line 71)
[Sat, 16 Feb 2013 12:16:05 +0000] INFO: template[/etc/chef-server/chef-server.rb] updated content
[Sat, 16 Feb 2013 12:16:05 +0000] INFO: template[/etc/chef-server/chef-server.rb] sending run action to execute[reconfigure-chef-server] (immediate)
[Sat, 16 Feb 2013 12:16:05 +0000] INFO: Processing execute[reconfigure-chef-server] action run (chef-server::default line 80)
[Sat, 16 Feb 2013 12:17:59 +0000] INFO: execute[reconfigure-chef-server] ran successfully
[Sat, 16 Feb 2013 12:17:59 +0000] INFO: Processing execute[reconfigure-chef-server] action nothing (chef-server::default line 80)
[Sat, 16 Feb 2013 12:17:59 +0000] INFO: Processing ruby_block[ensure node can resolve API FQDN] action create (chef-server::default line 85)
[Sat, 16 Feb 2013 12:17:59 +0000] INFO: Chef Run complete in 536.107466 seconds
[Sat, 16 Feb 2013 12:17:59 +0000] INFO: Running report handlers
[Sat, 16 Feb 2013 12:17:59 +0000] INFO: Report handlers complete



vagrant ssh

sudo cp /etc/chef-server/*.pem /vagrant/.chef/




knife configure -i

knife configure -i
WARNING: No knife configuration file found
Where should I put the config file? [/Users/leo/.chef/knife.rb] knife.rb
Please enter the chef server URL: [http://macbookproleo:4000] http://localhost:4000            
Please enter a clientname for the new client: [leo] 
Please enter the existing admin clientname: [chef-webui] admin
Please enter the location of the existing admin client's private key: [/etc/chef/webui.pem] keys/chef/client.pem
Please enter the validation clientname: [chef-validator] 
Please enter the location of the validation key: [/etc/chef/validation.pem] keys/chef/validation.pem
Please enter the path to a chef repository (or leave blank): 
Creating initial API user...
ERROR: knife encountered an unexpected error
This may be a bug in the 'configure' knife command or plugin
Please collect the output of this command with the `-VV` option before filing a bug report.
Exception: NoMethodError: undefined method `save' for #<Hash:0x007fa8fe123668>


cat .chef/knife.rb

log_level                :info
log_location             STDOUT
node_name                'admin'
client_key               '/Users/leo/programs/projects/chef-server-example/.chef/admin.pem'
validation_client_name   'chef-validator'
validation_key           '/Users/leo/programs/projects/chef-server-example/.chef/chef-validator.pem'
chef_server_url          'https://10.33.33.33'
syntax_check_cache_path  '/Users/leo/programs/projects/chef-server-example/.chef/syntax_check_cache'


https://10.33.33.33/version



knife client list
chef-validator
chef-webui


