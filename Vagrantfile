# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
apt-get install -qq tuxpaint

# put saved tuxpaint artwork to shared folder on host
if [ ! -d /vagrant/saved ]; then
  sudo -u vagrant mkdir /vagrant/saved
fi

if [ ! -d /home/vagrant/.tuxpaint ]; then
  sudo -u vagrant mkdir -p /home/vagrant/.tuxpaint
  sudo -u vagrant ln -s /vagrant/saved /home/vagrant/.tuxpaint/saved
fi
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "box-cutter/ubuntu1404-desktop"

  config.vm.provision "shell", inline: $script

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end
end
