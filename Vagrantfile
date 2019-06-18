# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|

    config.vm.box = "centos/7"

    # (1..3).each do |number|
    (1..2).each do |number|
        config.vm.define "n#{number}" do |node|
            node.vm.network "private_network", ip: "192.168.88.20#{number}"
            node.vm.network "forwarded_port", guest: 22, host: "228#{number}", id: "ssh"
            node.vm.hostname = "n#{number}"
        end  
    end

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024 
        v.cpus = 1
    end

    # config.ssh.username = 'root'
    # config.ssh.password = 'vagrant'
    config.ssh.insert_key = false

    id_rsa_key_pub = File.read(File.join(Dir.home, ".ssh/elastic-ansible-config", "elastic-ansible.pub"))
    config.vm.provision :shell,
        :inline => "echo 'appending SSH public key to ~vagrant/.ssh/authorized_keys' && echo '#{id_rsa_key_pub }' >> /home/vagrant/.ssh/authorized_keys && chmod 600 /home/vagrant/.ssh/authorized_keys"
    # config.vm.provision :shell,
    #     :inline => "echo 'appending SSH public key to root/.ssh/authorized_keys' && echo '#{id_rsa_key_pub }' >> /root/.ssh/authorized_keys && chmod 700 /root/.ssh/authorized_keys"
end
