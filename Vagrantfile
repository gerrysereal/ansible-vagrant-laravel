Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"  # Ubuntu 22.04
  config.vm.hostname = "laravel-dev"
  config.vm.network "private_network", ip: "192.168.56.10" 

  # Provisioning dengan Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision.yml"
  end

  # Optional: RAM & CPU
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end
end
