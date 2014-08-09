# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "hashicorp/precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
  end

  config.vm.network :private_network, ip: "192.168.13.37"
  config.vm.hostname = "dev.typo3.local"
  config.ssh.forward_agent = true

  config.vm.synced_folder "src/", "/var/www", type: "nfs", disabled: false

  config.vm.provider :virtualbox do |v|
    v.name = "TYPO3CMS"
    v.customize ["modifyvm", :id, "--memory", 1024]
    v.customize ["modifyvm", :id, "--cpus", 2]
  end

end
