# -*- mode: ruby -*-
# vi: set ft=ruby :

$targets_count = 3

if ENV['TARGETS'].to_i > 0 && ENV['TARGETS']
  $targets_count = ENV['TARGETS'].to_i
end

Vagrant.configure('2') do |config|
  config.vm.box = 'centos/7'
  config.ssh.forward_agent = true
  config.vm.network "private_network", type: "dhcp"

  (1..$targets_count).each do |i|
    config.vm.define "target#{i}"
  end

  config.vm.define :windows do |windows|
    windows.vm.box = "mwrock/WindowsNano"
    windows.vm.guest = :windows
    windows.vm.communicator = "winrm"
  end
end