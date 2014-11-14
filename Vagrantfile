# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # VM: Ubuntu 12.04 LTS
  config.vm.box = "hashicorp/precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  # check for box updates on each startup
  config.vm.box_check_update = true

  # configure VM via Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
  end

  # configure network
  config.vm.network :private_network, ip: "192.168.13.37"
  config.vm.hostname = "t3dev-#{rand(100000..999999)}"
  config.ssh.forward_agent = true

  # override provider settings
  config.vm.provider "virtualbox" do |virtualbox, override|
    override.vm.synced_folder "vHosts/", "/var/www/", id: "vagrant-root", type: "nfs", nfs_version: "3,nolock"

    virtualbox.customize ["modifyvm", :id, "--memory", 2048]
    virtualbox.customize ["modifyvm", :id, "--cpus", 2]
  end

  config.vm.provider "vmware_fusion" do |vmware_fusion, override|
    override.vm.synced_folder "vHosts/", "/var/www/", id: "vagrant-root", type: "nfs", nfs_version: "3,nolock"

    vmware_fusion.vmx["memsize"] = "2048"
    vmware_fusion.vmx["numvcpus"] = "2"
  end

  config.vm.provider "vmware_workstation" do |vmware_workstation, override|
    override.vm.synced_folder "vHosts/", "/var/www/", owner: "www-data", group: "www-data", type: "rsync"

    vmware_workstation.vmx["memsize"] = "2048"
    vmware_workstation.vmx["numvcpus"] = "2"
  end

end
