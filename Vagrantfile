VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.hostname = "devops-project"
  config.vm.box = "file:///home/franshesco/SysAdmin/Vagrant/Vagrant-Boxes/ubuntu-14.04-amd64-vbox-puppet-chef.box"

  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--memory", 512]
    v.customize ["modifyvm", :id, "--cpus", 1]
  end

  config.vm.network "forwarded_port", guest: 6000, host: 6000

  config.vm.provision "shell", inline: "cd /vagrant/chef-repo; make install-chef-client"
  config.vm.provision "chef_solo" do |chef|
     chef.cookbooks_path = ["chef-repo/site-cookbooks", "chef-repo/cookbooks"]
     chef.add_recipe "factorialapp"
  end

end
