# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

Vagrant.configure("2") do |config|

  config.vm.box = "debian/jessie64"
  config.vm.box_version = "8.5.0"

  # VirtualBox configuration
  config.vm.provider "virtualbox" do |v|
    # v.gui = true
    v.memory = 1024
    v.cpus = 1
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--audio", "none"]
    v.customize ["modifyvm", :id, "--usb", "off"]
    v.customize ["modifyvm", :id, "--usbehci", "off"]
    v.customize ["modifyvm", :id, "--vrde", "off"]
  end

  config.vm.define "golang" do |prj|
    prj.vm.hostname = "golang.local"
    prj.vm.network "private_network", ip: "192.168.1.10"
    #prj.ssh.guest_port = 2220
    #prj.vm.network :forwarded_port, guest: 22, host: 2220, id: 'ssh'
    prj.vm.synced_folder "/home/jebovic/projects/gosample", "/srv/golang", type: "nfs", nfs_udp: true
  end

  config.vm.define "ci" do |prj|
    prj.vm.hostname = "ci.local"
    prj.vm.network "private_network", ip: "192.168.1.20"
    #prj.ssh.guest_port = 2220
    #prj.vm.network :forwarded_port, guest: 22, host: 2220, id: 'ssh'
    #prj.vm.synced_folder "/home/jebovic/projects/gosample", "/srv/golang/src", type: "nfs", nfs_udp: true
  end

  config.vm.define "weblemp" do |prj|
    prj.vm.hostname = "weblemp.local"
    prj.vm.network "private_network", ip: "192.168.1.30"
    #prj.ssh.guest_port = 2220
    #prj.vm.network :forwarded_port, guest: 22, host: 2220, id: 'ssh'
    prj.vm.synced_folder "/home/jebovic/projects", "/srv/www", type: "nfs", nfs_udp: true
  end

  config.vm.define "weblamp" do |prj|
    prj.vm.hostname = "weblamp.local"
    prj.vm.network "private_network", ip: "192.168.1.31"
    #prj.ssh.guest_port = 2220
    #prj.vm.network :forwarded_port, guest: 22, host: 2220, id: 'ssh'
    prj.vm.synced_folder "/home/jebovic/projects", "/srv/www", type: "nfs", nfs_udp: true
  end

end