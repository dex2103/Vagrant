VAGRANT_COMMAND = ARGV[0]
 
Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-20.04"
 
  config.vm.provider "virtualbox" do |v|
    v.memory = 10240
    v.cpus = 3
  end
  config.vm.network "private_network", ip: "192.168.44.44"
 
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbooks/clone_roles.yml"
    ansible.extra_vars = {
      git_repository: "Repozytorium Ansible_roles",
      git_branch: "main"
    }
  end
 
  if VAGRANT_COMMAND == "ssh"
    config.ssh.username = 'panda'
  end
end