# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Forward ssh agent information (remote auth keys)
  config.ssh.forward_agent = true

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "precise64"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network :forwarded_port, guest: 80, host: 8080

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "../theme/wp", "/var/www/wp-content/theme"
  # Enable berkshelf plugin integration. The plugin will look in your current
  # working directory for your Berksfile by default. Just ensure that your
  # Berksfile exists and when you run vagrant up, vagrant provision, or vagrant
  # destroy the Berkshelf integration will automatically kick in!
  config.berkshelf.enabled = true

  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  #
  config.vm.provision :chef_solo do |chef|
    chef.json = {
      "nodejs" => {
        "version" => "0.10.16",
        "npm" => "1.3.8"
      },
      "wordpress" => {
        "password" => "password"
      }
    }
    chef.run_list = [
      "recipe[apt]",
      "recipe[nodejs]",
      "recipe[wordpress::default"
    ]
  end

end