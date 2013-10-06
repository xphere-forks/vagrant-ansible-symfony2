Vagrant.configure("2") do |setup|
  box = "http://cloud-images.ubuntu.com/vagrant/raring/current/raring-server-cloudimg-amd64-vagrant-disk1.box"

  setup.vm.define "web", primary: true do |config|
    config.vm.box = "raring64"
    config.vm.box_url = box
    config.vm.network :private_network, ip: "192.168.2.10"
    config.vm.network :public_network
    config.vm.synced_folder "..", "/projects", :nfs => true

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "devops/webserver.yml"
      ansible.inventory_path = "devops/hosts"
      ansible.verbose = "v"
    end
  end

  setup.vm.define "db" do |config|
    config.vm.box = "raring64"
    config.vm.box_url = box
    config.vm.network :private_network, ip: "192.168.2.20"
    config.vm.network :public_network

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "devops/dbserver.yml"
      ansible.inventory_path = "devops/hosts"
      ansible.verbose = "v"
    end
  end

end
