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
    vb.memory = 1024
    vb.cpus = 1
    vb.customize ["modifyvm", :id, '--audio', 'coreaudio', '--audiocontroller', 'hda'] # choices: hda sb16 ac97
  end

  ["vmware_fusion", "vmware_workstation"].each do |provider|
    config.vm.provider provider do |v, override|
      v.vmx["memsize"] = "1024"
      v.vmx["numvcpus"] = "1"
      v.vmx["sound.startconnected"] = "TRUE"
      v.vmx["sound.present"] = "TRUE"
      v.vmx["sound.autodetect"] = "TRUE"
    end
  end



end
