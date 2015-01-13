# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
VAGRANT_ROOT = File.dirname(__FILE__)

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "util" do |util|

    if Vagrant.has_plugin?("vagrant-cachier")
      util.cache.scope = :box
    end
    if Vagrant.has_plugin?("vagrant-vbguest")
      util.vbguest.auto_update = false
    end

    util.ssh.forward_agent = true
    util.vm.box = "centos65"
    util.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"

    util.vm.network :private_network, ip: "192.168.58.190"
    util.vm.hostname = "util.francotechnology.com"

    util.vm.synced_folder "../scripts/", "/home/vagrant/scripts/"

    util.vm.provision "ansible" do |ansible|
      ansible.playbook = "../ansible/masterbooks/util.yml"
      ansible.inventory_path = "../ansible/inventory/util"
      ansible.limit = 'util'
      # ansible.verbose = 'vvvv'

    end


    util.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    end
  end
end
