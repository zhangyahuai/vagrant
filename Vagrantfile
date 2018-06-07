# -*- mode: ruby -*-
# vi: set ft=ruby :
# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"
boxes = [
{
:name => "centos01",
:eth1 => "192.168.205.10",
:mem => "1024",
:cpu => "1"
},
{
:name => "centos02",
:eth1 => "192.168.205.11",
:mem => "1024",
:cpu => "1"
},
{
:name => "centos03",
:eth1 => "192.168.205.12",
:mem => "1024",
:cpu => "1"
},
]
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
config.vm.box = "centos7.2"
config.ssh.username = "vagrant"
config.ssh.password = "vagrant"
config.vm.synced_folder ".", "/vagrant", id: "share", disabled: false
boxes.each do |opts|
config.vm.box_check_update = false
config.vm.define opts[:name] do |config|
config.vm.hostname = opts[:name]
config.vm.provider "virtualbox" do |v|
v.customize ["modifyvm", :id, "--memory", opts[:mem]]
v.customize ["modifyvm", :id, "--cpus", opts[:cpu]]
end
config.vm.network :private_network, ip: opts[:eth1]
end
end
end