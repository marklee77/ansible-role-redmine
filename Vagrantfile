# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.provider "virtualbox" do |v|
    v.memory = 1280
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "getroles.yml"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.extra_vars = {
      gitlab_http_port: 8080,
      gitlab_enable_ssl: false,
      gitlab_require_ssl: false,
      gitlab_ssh_port: "{{ ansible_ssh_port }}"
    }
  end

end
