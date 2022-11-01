---
title: Vagrant
description: A quick summary of Vagrant
published: true
date: 2022-11-01T04:23:48.272Z
tags: 
editor: markdown
dateCreated: 2022-10-01T21:28:19.321Z
---

https://www.engineyard.com/blog/building-a-vagrant-box
# Kali
this box was made by a denhac member

u: vagrant p: vagrant

Vagrant Config for Kali
```
Vagrant.configure("2") do |config|
  config.vm.box = "evanplaice/Kali-Linux-2018.4-x64-MATE"
  config.vm.box_version = "1.0"
	
	config.vm.provider :virtualbox do |vb|
	    vb.name = "Kali"
			vb.gui = true
			vb.memory = "2048"
	end
end
```

# Commands
vagrant up - Starts the machines based on vagrantfile
vagrant status - Check the status
vagrant halt - will stop all the vms
vagrant destroy - Destroy the machines and delete disks