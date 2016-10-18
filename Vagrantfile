Vagrant.configure("2") do |config|

#########
# WWW01 #
#########

config.vm.synced_folder ".", "/vagrant", disabled: true

config.vm.define "www01" do |www01|

  www01.vm.box = "dummy"

#  www01.ssh.pty = "true"

  www01.vm.provider :aws do |aws, override|

  aws.tags = {
  'Name' => 'www01',
  'Type' => 'wordpress'
  }

  aws.access_key_id = ENV['AWS_ACCESS_KEY']
  aws.secret_access_key = ENV['AWS_SECRET_KEY']
  aws.ami = "ami-e8f3a4ff"
  aws.region = "us-east-1"
  aws.instance_type = "t2.nano"
  aws.security_groups = ["sg-d4d2a4b0"]
  aws.subnet_id = "subnet-6060ee39"
  aws.elb = "wordpress-elb"
  override.ssh.username = "hops"
  override.ssh.private_key_path = "~/.ssh/FrancoTech.pem"

  www01.vm.provision "ansible" do |ansible|
    ansible.playbook = "../ansible/webserver.yml"
    ansible.inventory_path = "../ansible/inventory/prod"
    ansible.limit = "wordpress"
  end

  end
  end
end
