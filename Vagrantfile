# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"


Vagrant.configure(VAGRANTFILE_API_VERSION) do |cluster|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.

cluster.vm.define "ansible-node" do |config|
  config.vm.box = "chef/centos-7.1"
  config.ssh.insert_key = false
  config.ssh.forward_agent = true
  config.vm.provider :virtualbox do |vb, override|
    vb.customize ["modifyvm", :id, "--memory", "128"]
    vb.customize ["modifyvm", :id, "--cpus", "1"]
  end
  config.vm.hostname = "ansible-node"
  config.vm.network :private_network, ip: "10.42.0.2"
end


cluster.vm.define "node-1" do |config|
  config.vm.box = "bento/centos-6.7"
  config.ssh.insert_key = false
  config.vm.provider :virtualbox do |vb, override|
    vb.customize ["modifyvm", :id, "--memory", "128"]
    vb.customize ["modifyvm", :id, "--cpus", "1"]
  end
  config.vm.hostname = "node-1"
  config.vm.network :private_network, ip: "10.42.0.6"
end

cluster.vm.define "node-2" do |config|
  config.vm.box = "bento/centos-6.7"
  config.ssh.insert_key = false
  config.vm.provider :virtualbox do |vb, override|
    vb.customize ["modifyvm", :id, "--memory", "128"]
    vb.customize ["modifyvm", :id, "--cpus", "1"]
  end
  config.vm.hostname = "node-2"
  config.vm.network :private_network, ip: "10.42.0.7"
end

cluster.vm.define "node-3" do |config|
  config.vm.box = "bento/ubuntu-12.04"
  config.ssh.insert_key = false
  config.vm.provider :virtualbox do |vb, override|
    vb.customize ["modifyvm", :id, "--memory", "128"]
    vb.customize ["modifyvm", :id, "--cpus", "1"]
  end
  config.vm.hostname = "node-3"
  config.vm.network :private_network, ip: "10.42.0.8"
end

cluster.vm.define "haproxy" do |config|
  config.vm.box = "bento/centos-6.7"
  config.ssh.insert_key = false
  config.vm.provider :virtualbox do |vb, override|
    vb.customize ["modifyvm", :id, "--memory", "128"]
    vb.customize ["modifyvm", :id, "--cpus", "1"]
  end
  config.vm.hostname = "haproxy"
  config.vm.network :private_network, ip: "10.42.0.100"
end

end
