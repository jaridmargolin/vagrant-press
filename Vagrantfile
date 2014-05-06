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
  config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network :forwarded_port, guest: 80, host: 8080

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder "../wordpress", "/var/www/wordpress"

  # Enable berkshelf plugin integration. The plugin will look in your current
  # working directory for your Berksfile by default. Just ensure that your
  # Berksfile exists and when you run vagrant up, vagrant provision, or vagrant
  # destroy the Berkshelf integration will automatically kick in!
  config.berkshelf.enabled = true

  # Lets get an up to date chef installation
  config.omnibus.chef_version = "11.6.0"

  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  config.vm.provision :chef_solo do |chef|
    chef.json = {
      "build_essential" => {
        "compiletime" => true
      },
      "mysql"=> {
        "server_root_password" => "password",
        "server_repl_password" => "password",
        "server_debian_password" => "password"
      },
      "apache"=> {
        "user" => "vagrant",
        "group" => "vagrant"
      },
      "wordpress" => {
        "password" => "password"
      }
    }
    chef.run_list = [
      "recipe[build-essential]",
      "recipe[apt]",
      "recipe[wordpress::default]"
    ]
  end

end