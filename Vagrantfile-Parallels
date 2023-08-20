Vagrant.configure("2") do |config|
  config.vm.box = "almalinux/9.aarch64"
  config.ssh.insert_key = false
  config.proxy.http     = "http://10.0.1.5:3128"
  config.proxy.https     = "http://10.0.1.5:3128"
  config.proxy.no_proxy = "localhost,127.0.0.1"
  config.vm.synced_folder ".", "/vagrant", disabled: true

    # Parallels Only 
    config.vm.provider "parallels" do |prl|
      prl.cpus = 1
      #prl.memory = 512
    end

    # webserver01
    config.vm.define "webserver01" do |www1|
      www1.vm.hostname = "webserver01"
      www1.vm.network :private_network, ip: "192.168.2.101"
    end
  
    # webserver02
    config.vm.define "webserver02" do |www2|
      www2.vm.hostname = "webserver02"
      www2.vm.network :private_network, ip: "192.168.2.102"
    end
    
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL

   #Ansible provision
   config.vm.provision "ansible" do |ansible|
     ansible.playbook = "main.yml"
     ansible.become = true
     ansible.inventory_path = "inventory"
     ansible.limit = "all"
     ansible.extra_vars = {
       ansible_user: 'vagrant',
       ansible_ssh_private_key_file: "~/.vagrant.d/insecure_private_key"
     }
   end

end
