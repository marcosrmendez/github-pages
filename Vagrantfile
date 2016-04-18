# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "jekyll-github-pages"
  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  config.vm.box_check_update = true

  #uncomment this to map the jekyll server port
  #config.vm.network "forwarded_port", guest: 4000, host: 4000

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  # config.vm.network "public_network"

  #uncomment this to share the ssh keys from your host box
  #config.vm.synced_folder "~/.ssh", "/home/vagrant/.ssh"

  config.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", 512]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  config.push.define "atlas" do |push|
     push.app = "marcosrmendez/github-pages"
  end

  config.vm.provision "shell", privileged: false, path: "script/vagrant"

  #uncomment this to start the jekyll server automatically
  #config.vm.provision "shell", privileged: false, path: "script/server", run: "always"

  #uncomment this to set the git user and email from your host box
  #if File.exists?(File.join(Dir.home, ".gitconfig"))
  #  git_name = `git config user.name`   # find locally set git name
  #  git_email = `git config user.email` # find locally set git email
  #  # set git name for 'vagrant' user on VM
  #  config.vm.provision :shell, :inline => "echo 'Saving local git username to VM...' && sudo -i -u vagrant git config --global user.name '#{git_name.chomp}'"
    # set git email for 'vagrant' user on VM
  #  config.vm.provision :shell, :inline => "echo 'Saving local git email to VM...' && sudo -i -u vagrant git config --global user.email '#{git_email.chomp}'"
  #end

end
