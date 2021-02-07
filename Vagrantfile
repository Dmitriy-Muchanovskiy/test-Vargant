# -*- mode: ruby -*-
# vi: set ft=ruby :
$vm_quantity = 2

Vagrant.configure(2) do |config|
  config.vm.provider "virualbox" do |vb|
     vb.gui = false
     vb.memory = "512"
     vb.cpus=1
     vb.check_guest_additions=false
  config.vm.box = "debian/buster64"
  config.vm.box_check_update = false
  end

  (1..$vm_quantity).each do |i|
    config.vm.define "vm#{i}" do |vms|
        vms.vm.hostname = "vm#{i}"  
        vms.vm.network "private_network", ip: "192.168.1.#{10+i}"
    end
  end  

  config.vm.provision "ansible" do|ansible|
    ansible.playbook = "playbook.yml"
  end
end
