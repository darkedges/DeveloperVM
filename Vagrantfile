# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vbguest.auto_update = true
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = false
  config.hostmanager.manage_guests = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/development-playbook.yml" 
    ansible.galaxy_role_file = "ansible/development-galaxy.yml"
    ansible.galaxy_command = "ansible-galaxy install --role-file=%{role_file}"
    ansible.verbose=""
    ansible.groups = {
      "development"   => [ "development" ]
    }
  end  

  config.vm.define "development" , autostart: true, primary: true do |development|
    development.vm.box = "centos/7"
    development.vm.hostname = "development"
    development.vm.network :private_network, ip: "192.168.50.101"
    development.vm.synced_folder "c:/development", "/development"
    development.vm.provider  "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--name", "development"]
      vb.customize ["modifyvm", :id, "--cpus", "1"]
      vb.customize ["modifyvm", :id, "--ioapic", "on"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "75"]
      vb.customize ["modifyvm", :id, "--paravirtprovider", "kvm"]
    end
  end
end
