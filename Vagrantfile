# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
VAGRANT_ROOT = File.dirname(__FILE__)

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "util01" do |util01|

    if Vagrant.has_plugin?("vagrant-cachier")
      util01.cache.scope = :box
    end
    if Vagrant.has_plugin?("vagrant-vbguest")
      util01.vbguest.auto_update = false
    end

    util01.ssh.forward_agent = true
    util01.vm.box = "centos65"
    util01.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"

    util01.vm.network :private_network, ip: "192.168.58.190"
    util01.vm.hostname = "util01.francotechnology.com"

    util01.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    end

  end

end
