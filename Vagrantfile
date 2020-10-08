# Master vars
$install_ansible = <<-SCRIPT
  sudo dnf install -y epel-release && sudo dnf install -y ansible && \
  mkdir /home/vagrant/keys
SCRIPT

$change_sshd_config = <<-SCRIPT
  sudo sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config && \
  sudo sed -i 's/#PubkeyAuthentication yes/PubkeyAuthentication yes/' /etc/ssh/sshd_config
SCRIPT

Vagrant.configure("2") do |config|
    config.vm.provider "virtualbox" do |v|
      v.memory = 1024
    end
    config.vm.synced_folder ".vagrant/machines/", "/home/vagrant/.vagrant"
    config.vm.synced_folder ".", "/vagrant", disabled: true

    # Box de Ansible (master)
    config.vm.define 'master' do |master|
        master.vm.box = "generic/centos8"
        master.vm.synced_folder ".", "/home/vagrant/host"
        master.vm.synced_folder ".", "/vagrant", disabled: true
        master.vm.provider "virtualbox" do |v|
          v.memory = 4096
        end
  
        master.vm.provision "shell", inline: "echo alias clear_hosts='> /home/vagrant/.ssh/known_hosts' >> /home/vagrant/.bashrc"
        master.vm.provision "shell", inline: $install_ansible, privileged: false 
        master.vm.provision "shell", inline: $change_sshd_config, privileged: false
  
        master.vm.network "private_network", ip: "172.17.167.11"
        master.vm.hostname = 'centos-master.local'
    end
    
    
    # --------------------------------------------------------------------------------------------------------------------------------------------
    config.vm.define 'docker-0' do |docker_node0|
        docker_node0.vm.box = "generic/centos8"
        docker_node0.vm.synced_folder ".", "/home/vagrant/host"
        docker_node0.vm.synced_folder ".", "/vagrant", disabled: true
        docker_node0.vm.provider "virtualbox" do |v|
          v.memory = 1024
        end

        docker_node0.vm.provision "shell", inline: $change_sshd_config, privileged: false
              
        docker_node0.trigger.after :up do |trigger|
          trigger.warn = "Docker node online!"
        end
        docker_node0.vm.network "private_network", ip: "172.17.167.12"
        docker_node0.vm.hostname = 'centos-docker-0.local'
    end
    
    
    # --------------------------------------------------------------------------------------------------------------------------------------------
end