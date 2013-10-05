Vagrant::Config.run do |setup|

  setup.vm.define "web" do |config|
    config.vm.box = "raring64"
    config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/raring/current/raring-server-cloudimg-amd64-vagrant-disk1.box"
    config.vm.forward_port 80, 8080
    config.vm.forward_port 443, 4443
    config.vm.network :bridged
    config.vm.network :hostonly, "192.168.2.10"

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "devops/webserver.yml"
      ansible.inventory_path = "devops/hosts"
    end
  end

  setup.vm.define "db" do |config|
    config.vm.box = "raring64"
    config.vm.box_url = "http://cloud-images.ubuntu.com/vagrant/raring/current/raring-server-cloudimg-amd64-vagrant-disk1.box"
    config.vm.forward_port 3306, 33306
    config.vm.network :bridged
    config.vm.network :hostonly, "192.168.2.20"

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "devops/dbserver.yml"
      ansible.inventory_path = "devops/hosts"
    end
  end

end
