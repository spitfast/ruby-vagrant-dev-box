# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.network "private_network", ip: "192.168.33.10"

  # config.ssh.forward_agent = true

  config.vm.synced_folder "./data", "/vagrant_data", type: 'nfs'

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
    vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
  end

  # ansible provision
  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = './playbook.yml'
  end
end
