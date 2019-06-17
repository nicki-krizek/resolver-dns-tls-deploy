# -*- mode: ruby -*-
# vi: set ft=ruby :
#

Vagrant.configure(2) do |config|

    config.vm.box = "debian/stretch64"

    config.vm.define "resolver-dns-tls"  do |vm|
        vm.vm.provision "ansible" do |ansible|
            ansible.playbook = "./setup.yaml"
        end
    end

    config.vm.synced_folder ".", "/vagrant", disabled: true

end
