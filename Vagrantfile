Vagrant.configure("2") do |config|
  config.vm.box = "almalinux/9.aarch64"
  config.proxy.http     = "http://10.0.1.5:3128"
  config.proxy.https     = "http://10.0.1.5:3128"
  config.proxy.no_proxy = "localhost,127.0.0.1"
  config.vm.synced_folder ".", "/vagrant", disabled: true

    # webserver01
    config.vm.define "webserver01" do |www1|
      www1.vm.hostname = "webserver01"
      www1.vm.network :private_network, ip: "192.168.2.101"
      config.vm.provider "parallels" do |prl|
        prl.name = "Homelab webserver01"
      end
    end
  
    # webserver02
    config.vm.define "webserver02" do |www1|
      www1.vm.hostname = "webserver02"
      www1.vm.network :private_network, ip: "192.168.2.102"
      config.vm.provider "parallels" do |prl|
        prl.name = "Homelab webserver02"
      end
    end
    
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL

   Ansible provision
   config.vm.provision "ansible" do |ansible|
     ansible.playbook = "main.yml"
     ansible.become = true
  # end

end
