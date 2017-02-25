# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
 
  config.vm.box = "centos/7"

  # Forward the Rails server default port to the host
  config.vm.network :forwarded_port, guest: 3000, host: 3000
  config.vm.provision "shell",
    inline: "yum -y install sqlite-devel; yum -y update"
  # Use Chef Solo to provision our virtual machine
  config.vm.provision :chef_solo do |chef|
    config.vm.synced_folder "src/", "/vagrant"

    chef.cookbooks_path = ["cookbooks", "site-cookbooks"]
    chef.channel = :stable
    chef.version = '12.10.24'

    chef.add_recipe "nodejs"
    chef.add_recipe "ruby_build"
    chef.add_recipe "ruby_rbenv::user"
    chef.add_recipe "vim"

    # Install Ruby 2.2.2 and Bundler
    # Set an empty root password for MySQL to make things simple
    chef.json = {
      rbenv: {
        user_installs: [{
          user: 'vagrant',
          rubies: ["2.2.2"],
          global: "2.2.2",
          gems: {
            "2.2.2" => [
              { name: "bundler" },
              { name: "rails" },
              { name: "twitter" },
              { name: "spork-rails"},
              { name: "sqlite3" }                          
            ]
          }
        }]
      }
    }
  end
end
