Vagrant::Config.run do |config|

  config.vm.define :web do |web_config|
    web_config.vm.box = "raring64"
    web_config.vm.box_url = 'http://cloud-images.ubuntu.com/vagrant/raring/current/raring-server-cloudimg-amd64-vagrant-disk1.box'
    web_config.vm.forward_port 80, 8080
    web_config.vm.forward_port 443, 4443
    web_config.vm.network :bridged
    web_config.vm.network :hostonly, "192.168.2.10"

    web_config.vm.provision :ansible do |ansible|
      ansible.playbook = "devops/webserver.yml"
      ansible.hosts = "webservers"
      ansible.inventory_file = "devops/hosts"
    end
  end

  config.vm.define :db do |db_config|
    db_config.vm.box = "raring64"
    db_config.vm.box_url = 'http://cloud-images.ubuntu.com/vagrant/raring/current/raring-server-cloudimg-amd64-vagrant-disk1.box'
    db_config.vm.forward_port 3306, 33306
    db_config.vm.network :bridged
    db_config.vm.network :hostonly, "192.168.2.20"

    db_config.vm.provision :ansible do |ansible|
      ansible.playbook = "devops/dbserver.yml"
      ansible.hosts = "dbservers"
      ansible.inventory_file = "devops/hosts"
    end
  end

end