# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
VAGRANT_ROOT = File.dirname(__FILE__)

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "bare" do |bare|

    if Vagrant.has_plugin?("vagrant-cachier")
      bare.cache.scope = :box
    end
    if Vagrant.has_plugin?("vagrant-vbguest")
      bare.vbguest.auto_update = false
    end

    bare.ssh.forward_agent = true
    bare.vm.box = "centos65"
    bare.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"

    bare.vm.network :private_network, ip: "192.168.56.190"
    bare.vm.hostname = "dev.bare.francotechnology.com"

    bare.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    end

  end

end

