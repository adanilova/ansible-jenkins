# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
        config.vm.box = "centos/7"
        config.vm.box_check_update = false
        config.vm.hostname = "jenkins"

        config.vm.network :private_network, ip: "192.168.13.13"
        config.vm.provision :shell, :inline => "sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config; sudo systemctl restart sshd;", run: "always"
        config.vm.provision "file", source: "~/.ssh/vagrant.pub", destination: "/home/vagrant/.ssh/authorized_keys"

end
# Run commands as root.
