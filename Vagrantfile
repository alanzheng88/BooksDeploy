# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "dummy"

  config.vm.provider :aws do |aws, override|
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    # security group must have ssh port opened
    aws.security_groups = ENV['AWS_SECURITY_GROUPS']
    aws.subnet_id = ENV['AWS_SUBNET_ID']
    aws.elastic_ip = ENV['AWS_ELASTIC_IP']
    aws.keypair_name = ENV['AWS_KEYPAIR_NAME']
    aws.region = 'us-west-2'
    aws.instance_type = 't2.micro'
    aws.terminate_on_shutdown = false

    # CentOS 7 (x86_64) - with Updates HVM
    aws.ami = "ami-3ecc8f46"

    # this user is a mandatory requirement for this CentOS 7 image
    override.ssh.username = "centos"
    override.ssh.private_key_path = ENV['AWS_PRIVATE_KEY_PATH']
    override.nfs.functional = false
    # /vagrant folder will be synced by default for aws
    override.vm.allowed_synced_folder_types = [:rsync]
  end

  # Run Ansible from Vagrant host
  config.vm.provision :ansible do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.playbook = "ansible/playbook.yml"
  end
end
