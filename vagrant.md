<!-- TITLE: Vagrant -->
<!-- SUBTITLE: A quick summary of Vagrant -->


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