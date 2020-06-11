# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "bento/ubuntu-18.04"
    config.vm.box_check_update = false
    config.vm.hostname = "mylamp73"
    config.vm.boot_timeout = 1800 # 30 minutes

    # automatic guest plugin update disabled
    if Vagrant.has_plugin?("vagrant-vbguest")
        config.vbguest.auto_update = false
    end

    # config.vm.network "forwarded_port", guest: 80, host: 8080
    config.vm.network "private_network", ip: "192.168.33.10"
    config.vm.synced_folder ".", "/var/www", :mount_options => ["dmode=777", "fmode=766"]
    config.ssh.insert_key = false

    # VirtualBox specific settings
    config.vm.provider "virtualbox" do |virtualbox|
        # friendly name of the virtual machine
        virtualbox.name = "MyLamp73"
        # Hide/show the VirtualBox GUI when booting the machine
        virtualbox.gui = true
        # Customize the amount of memory 4GB on the VM:
        virtualbox.memory = 4096
        # Use 2 CPUs in the VM:
        virtualbox.cpus = 2
    end

    config.vm.provision "shell", path: "install.sh", privileged: false

end
