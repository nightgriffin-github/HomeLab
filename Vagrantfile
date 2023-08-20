Vagrant.configure("2") do |config|
  config.vm.box = "generic/centos8"
  config.ssh.insert_key = false
  config.proxy.http     = "http://10.0.1.5:3128"
  config.proxy.https     = "http://10.0.1.5:3128"
  config.proxy.no_proxy = "localhost,127.0.0.1"

  config.vm.define "webserver01" do |webserver01|
    webserver01.vm.hostname = "webserver01"
    webserver01.vm.network :private_network, :ip => "192.168.2.101"
    webserver01.vm.provider "libvirt" do |libvirt|
      libvirt.memory = 2048 
      libvirt.cpus = 2
    end
  end

  config.vm.define "webserver02" do |webserver02|
    webserver02.vm.hostname = "webserver02"
    webserver02.vm.network :private_network, :ip => "192.168.2.102"
    webserver02.vm.provider "libvirt" do |libvirt|
      libvirt.memory = 2048
      libvirt.cpus = 2
    end
  end

   #Ansible provision
   #config.vm.provision "ansible" do |ansible|
   #  ansible.playbook = "main.yml"
   #  ansible.become = true
   #  ansible.inventory_path = "inventory"
   #  ansible.limit = "all"
   #  ansible.extra_vars = {
   #    ansible_user: 'vagrant',
   #    ansible_ssh_private_key_file: "~/.vagrant.d/insecure_private_key"
   #  }
   #end

end
