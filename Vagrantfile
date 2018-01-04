# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/7"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.provider "virtualbox" do |vb|
    config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
  end

  config.vm.provision :ansible_local do |ansible|
    ansible.galaxy_role_file = "playbooks/requirements.yml"
    ansible.playbook = "playbooks/install.yml"
    ansible.install  = true
  end
end
