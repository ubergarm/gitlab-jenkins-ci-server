# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.define :ci do |ci_config|
    ci_config.vm.box = "precise32"
    config.vm.box_url = "http://files.vagrantup.com/precise32.box"
    ci_config.vm.network :forwarded_port, host: 8000, guest: 80
    ci_config.vm.network :forwarded_port, host: 8080, guest: 8080
    ci_config.vm.network :private_network, ip: "192.168.33.103"
    #ci_config.vm.synced_folder "./data", "/vagrant_data"

    #the bootstrap script installs ansible in the VM itself    
    ci_config.vm.provision :shell, :path => "bootstrap.sh"

    ci_config.vm.provider :virtualbox do |vb|
      #vb.gui = true
      vb.customize [
		    "modifyvm", :id,
		    "--name", "gitlab-jenkins-ci-server",
		    "--memory", "2048"
	 	   ]
    end
  end
end
