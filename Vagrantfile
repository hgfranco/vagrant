# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
VAGRANT_ROOT = File.dirname(__FILE__)

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

#config.ssh.insert_key = false

#config.ssh.private_key_path = File.expand_path('~/.vagrant.d/insecure_private_key')

#config.ssh.keys_only = true

########
# UTIL #
########

config.vm.define "util" do |util|
    util.ssh.insert_key = false

    if Vagrant.has_plugin?("vagrant-cachier")
      util.cache.scope = :box
    end
    if Vagrant.has_plugin?("vagrant-vbguest")
      util.vbguest.auto_update = false
    end

    util.vm.network :private_network, ip: "10.1.1.2"
    util.vm.hostname = "vg-util01.francotechnology.com"

    #util.vm.network :forwarded_port, guest: 80, host: 1234

    util.ssh.forward_agent = true
    util.vm.box = "centos7"
    #util.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.4.2/centos64-x86_64-20140116.box"
    #util.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"
    util.vm.box_url = "http://cloud.centos.org/centos/7/vagrant/x86_64/images/CentOS-7-x86_64-Vagrant-1610_01.VirtualBox.box"

    #util.vm.synced_folder "~/Downloads", ""

    util.vm.provision "ansible" do |ansible|
      ansible.playbook = "../ansible/playbooks/util.yml"
      ansible.inventory_path = "../ansible/inventory/development"
      ansible.limit = 'util'
      ansible.raw_arguments  = "--vault-password-file=~/.vault_pass.txt" 
    end

    util.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    end
end
end
