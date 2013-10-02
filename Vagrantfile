# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.provision :shell, :inline => <<-EOS
    sudo apt-get update
    sudo apt-get install -y ruby1.9.3
    sudo update-alternatives --install /usr/bin/ruby ruby /usr/bin/ruby1.9.3 400
    sudo gem install engineyard
    EOS
end
