# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
VAGRANT_ROOT = File.dirname(__FILE__)

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

#config.ssh.insert_key = false

#config.ssh.private_key_path = File.expand_path('~/.vagrant.d/insecure_private_key')


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

    util.ssh.forward_agent = true
    util.vm.box = "centos65"
    util.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"

    util.vm.network :private_network, ip: "10.1.1.1"
    util.vm.hostname = "util01.francotechnology.com"

    util.vm.synced_folder "../scripts/", "/home/vagrant/scripts/"

    util.vm.provision "ansible" do |ansible|
      ansible.playbook = "../ansible/masterbooks/util.yml"
      ansible.inventory_path = "../ansible/inventory/development"
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


###########
# WWW_DEV #
###########

config.vm.define "www" do |www|

    www.ssh.insert_key = false


www.ssh.private_key_path = File.expand_path('/Users/hfranco/.vagrant.d/insecure_private_key')

    if Vagrant.has_plugin?("vagrant-cachier")
      www.cache.scope = :box
    end
    if Vagrant.has_plugin?("vagrant-vbguest")
      www.vbguest.auto_update = false
    end

    www.ssh.forward_agent = true
    www.vm.box = "centos65"
    www.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"

    www.vm.network :private_network, ip: "10.1.1.2"
    www.vm.hostname = "www01.francotechnology.com"

    #www.vm.synced_folder "../scripts/", "/home/vagrant/scripts/"

    www.vm.provision "ansible" do |ansible|
      ansible.playbook = "../ansible/masterbooks/www_dev.yml"
      ansible.inventory_path = "../ansible/inventory/development"
      ansible.limit = 'www'
      # ansible.verbose = 'vvvv'
    end

    www.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    end
end

##########
# WWW_DB #
##########

config.vm.define "www_db" do |wwwdb|

    wwwdb.ssh.insert_key = false

    if Vagrant.has_plugin?("vagrant-cachier")
      wwwdb.cache.scope = :box
    end
    if Vagrant.has_plugin?("vagrant-vbguest")
      wwwdb.vbguest.auto_update = false
    end

    wwwdb.ssh.forward_agent = true
    wwwdb.vm.box = "centos65"
    wwwdb.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"

    wwwdb.vm.network :private_network, ip: "10.1.1.3"
    wwwdb.vm.hostname = "www-db01.francotechnology.com"

    #wwwdb.vm.synced_folder "../scripts/", "/home/vagrant/scripts/"

    wwwdb.vm.provision "ansible" do |ansible|
      ansible.playbook = "../ansible/masterbooks/www_db.yml"
      ansible.inventory_path = "../ansible/inventory/development"
      ansible.limit = 'www_db'
      # ansible.verbose = 'vvvv'
    end

    wwwdb.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    end
end
end
