VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "debian/jessie64"

  config.vm.provider :virtualbox do |v|
  config.vm.network "forwarded_port", guest: 80, host: 8080
  end
 
	
  config.vm.provision "shell", inline: 
    $script = <<SCRIPT
    echo Shell provisioning...
    sudo apt-get install puppet -y
SCRIPT

  config.vm.provision "puppet" do |puppet|
    puppet.manifests_path = "manifests"
    puppet.manifest_file = "default.pp"
    puppet.options = '--test'    # see the output
  end
end
