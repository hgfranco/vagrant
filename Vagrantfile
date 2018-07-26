Vagrant.configure("2") do |config|
  config.ssh.pty = true

############
# MASTER01 #
############


  config.vm.define "master01" do |master01|
  master01.vm.box = "dummy"

  master01.ssh.pty = true

  master01.vm.provider :aws do |aws, override|
    config.ssh.pty = true
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    aws.region = "us-east-1"
    aws.instance_type = "t2.micro"
    aws.security_groups = ["sg-d4d2a4b0"]
    aws.subnet_id = "subnet-6060ee39"
#   aws.elb = "wordpress-elb"
    aws.ami = "ami-22d68434"
    aws.elastic_ip = "34.226.96.237"
    override.ssh.username = "hops"
    override.ssh.private_key_path = "~/.ssh/FrancoTech.pem"


    master01.vm.provision "ansible" do |ansible|
      ansible.playbook = "../ansible/playbooks/mesos.yml"
      ansible.inventory_path = "../ansible/inventory/development"
      ansible.limit = 'vg-master01.francotechnology.com'
      ansible.raw_arguments = [ 
        "--private-key=~/.ssh/FrancoTech.pem",
        "--user=hops"
     ]
    end

  
    aws.tags = {
     'Name' => 'master01',
     'Type' => 'mesos'
    }
  end
end


############
# MASTER02 #
############


  config.vm.define "master02" do |master02|
  master02.vm.box = "dummy"

  master02.ssh.pty = true

  master02.vm.provider :aws do |aws, override|
    config.ssh.pty = true
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    aws.region = "us-east-1"
    aws.instance_type = "t2.micro"
    aws.security_groups = ["sg-d4d2a4b0"]
    aws.subnet_id = "subnet-6060ee39"
#   aws.elb = "wordpress-elb"
    aws.ami = "ami-22d68434"
    override.ssh.username = "hops"
    override.ssh.private_key_path = "~/.ssh/FrancoTech.pem"
  
    aws.tags = {
     'Name' => 'master02',
     'Type' => 'mesos'
    }
  end
end

############
# MASTER03 #
############


  config.vm.define "master03" do |master03|
  master03.vm.box = "dummy"

  master03.ssh.pty = true

  master03.vm.provider :aws do |aws, override|
    config.ssh.pty = true
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    aws.region = "us-east-1"
    aws.instance_type = "t2.micro"
    aws.security_groups = ["sg-d4d2a4b0"]
    aws.subnet_id = "subnet-6060ee39"
#   aws.elb = "wordpress-elb"
    aws.ami = "ami-22d68434"
    override.ssh.username = "hops"
    override.ssh.private_key_path = "~/.ssh/FrancoTech.pem"
  
    aws.tags = {
     'Name' => 'master03',
     'Type' => 'mesos'
    }
  end
end

############
# SLAVE01 #
############


  config.vm.define "slave01" do |slave01|
  slave01.vm.box = "dummy"

  slave01.ssh.pty = true

  slave01.vm.provider :aws do |aws, override|
    config.ssh.pty = true
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    aws.region = "us-east-1"
    aws.instance_type = "t2.micro"
    aws.security_groups = ["sg-d4d2a4b0"]
    aws.subnet_id = "subnet-6060ee39"
#   aws.elb = "wordpress-elb"
    aws.ami = "ami-22d68434"
    override.ssh.username = "hops"
    override.ssh.private_key_path = "~/.ssh/FrancoTech.pem"
  
    aws.tags = {
     'Name' => 'slave01',
     'Type' => 'mesos'
    }
  end
end

###########
# SLAVE02 #
###########


  config.vm.define "slave02" do |slave02|
  slave02.vm.box = "dummy"

  slave02.ssh.pty = true

  slave02.vm.provider :aws do |aws, override|
    config.ssh.pty = true
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    aws.region = "us-east-1"
    aws.instance_type = "t2.micro"
    aws.security_groups = ["sg-d4d2a4b0"]
    aws.subnet_id = "subnet-6060ee39"
#   aws.elb = "wordpress-elb"
    aws.ami = "ami-22d68434"
    override.ssh.username = "hops"
    override.ssh.private_key_path = "~/.ssh/FrancoTech.pem"
  
    aws.tags = {
     'Name' => 'slave02',
     'Type' => 'mesos'
    }
  end
end

###########
# SLAVE03 #
###########


  config.vm.define "slave03" do |slave03|
  slave03.vm.box = "dummy"

  slave03.ssh.pty = true

  slave03.vm.provider :aws do |aws, override|
    config.ssh.pty = true
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    aws.region = "us-east-1"
    aws.instance_type = "t2.micro"
    aws.security_groups = ["sg-d4d2a4b0"]
    aws.subnet_id = "subnet-6060ee39"
#   aws.elb = "wordpress-elb"
    aws.ami = "ami-22d68434"
    override.ssh.username = "hops"
    override.ssh.private_key_path = "~/.ssh/FrancoTech.pem"
  
    aws.tags = {
     'Name' => 'slave03',
     'Type' => 'mesos'
    }
  end
end

#########
# KAFKA #
#########

config.vm.define "kafka" do |kafka|
    kafka.ssh.insert_key = false

    if Vagrant.has_plugin?("vagrant-cachier")
      kafka.cache.scope = :box
    end
    if Vagrant.has_plugin?("vagrant-vbguest")
      kafka.vbguest.auto_update = false
    end

    kafka.vm.network "public_network", ip: "10.0.1.6"

    kafka.ssh.forward_agent = true
    kafka.vm.box = "centos7"
    # kafka.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.4.2/centos64-x86_64-20140116.box"
    #kafka.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"
    kafka.vm.box_url = "http://cloud.centos.org/centos/7/vagrant/x86_64/images/CentOS-7-x86_64-Vagrant-1610_01.VirtualBox.box"

#    kafka.vm.synced_folder "/Users/hfranco/sailthru", "/home/vagrant/sailthru"

    kafka.vm.provision "ansible" do |ansible|
      ansible.playbook = "../ansible/playbooks/kafka.yml"
      ansible.inventory_path = "../ansible/inventory/development"
      ansible.limit = 'kafka'
    end

    kafka.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    end
end

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

    util.vm.network :private_network, ip: "10.1.1.3"
    util.vm.hostname = "vg-sail01.francotechnology.com"

#util.vm.network :forwarded_port, guest: 22, host: 1234

    config.ssh.private_key_path = "~/.ssh/git_repo_user"
    config.ssh.private_key_path = "~/.vagrant.d/insecure_private_key"
    util.ssh.forward_agent = true
    util.vm.box = "centos7"
    #util.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.4.2/centos64-x86_64-20140116.box"
    #util.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"
    util.vm.box_url = "http://cloud.centos.org/centos/7/vagrant/x86_64/images/CentOS-7-x86_64-Vagrant-1610_01.VirtualBox.box"

    #util.vm.synced_folder "~/Downloads", ""

    util.vm.provision "ansible" do |ansible|
      ansible.playbook = "../ansible/playbooks/util.yml"
      ansible.inventory_path = "../ansible/inventory/development"
      ansible.limit = 'vg-sail01.francotechnology.com'
      ansible.raw_arguments  = "--vault-password-file=~/.vault_pass_util.txt"
    end

    util.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    end
end
end
