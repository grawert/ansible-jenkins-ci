# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.ssh.forward_agent = true

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.limit = "all"
    ansible.groups   = {
      "ldap_server"    => ["jenkins-master"],
      "jenkins_master" => ["jenkins-master"],
      "jenkins_slave"  => ["diskimage-builder"]
    }
    ansible.host_vars = {
      "diskimage-builder" => {"label" => "DIB"}
    }
  end

  config.vm.define "jenkins-master" do |master|
    master.vm.box = "centos/7"
    master.vm.network "private_network", ip: "192.168.11.10", :netmask => "255.255.255.0"
    master.vm.hostname = "jenkins-master"
    master.vm.provider "virtualbox" do |vb|
      vb.gui    = false
      vb.memory = "1024"
      vb.cpus   = 2
    end
  end

  config.vm.define "diskimage-builder" do |slave|
    slave.vm.box = "centos/7"
    slave.vm.network "private_network", ip: "192.168.11.11", :netmask => "255.255.255.0"
    slave.vm.hostname = "diskimage-builder"
    slave.vm.provider "virtualbox" do |vb|
      vb.gui    = false
      vb.memory = "512"
      vb.cpus   = 1
    end
  end

end
