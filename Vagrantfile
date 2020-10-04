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
    config.vm.define 'docker-1', autostart: false do |docker_node1|
        docker_node1.vm.box = "generic/centos8"
        docker_node1.vm.synced_folder ".", "/home/vagrant/host"
        docker_node1.vm.synced_folder ".", "/vagrant", disabled: true
        docker_node1.vm.provider "virtualbox" do |v|
          v.memory = 1024
        end

        docker_node1.vm.provision "shell", inline: $change_sshd_config, privileged: false

        docker_node1.trigger.after :up do |trigger|
          trigger.warn = "Docker node online!"
        end
        docker_node1.vm.network "private_network", ip: "172.17.167.13"
        docker_node1.vm.hostname = 'centos-docker-1.local'
    end
    
    
    # --------------------------------------------------------------------------------------------------------------------------------------------
    config.vm.define 'docker-2', autostart: false do |docker_node2|
        docker_node2.vm.box = "generic/centos8"
        docker_node2.vm.synced_folder ".", "/home/vagrant/host"
        docker_node2.vm.synced_folder ".", "/vagrant", disabled: true
        docker_node2.vm.provider "virtualbox" do |v|
          v.memory = 1024
        end

        docker_node2.vm.provision "shell", inline: $change_sshd_config, privileged: false

        docker_node2.trigger.after :up do |trigger|
          trigger.warn = "Docker node online!"
        end
        docker_node2.vm.network "private_network", ip: "172.17.167.14"
        docker_node2.vm.hostname = 'centos-docker-2.local'
    end
    
    
    # --------------------------------------------------------------------------------------------------------------------------------------------
    config.vm.define 'docker-3', autostart: false do |docker_node3|
        docker_node3.vm.box = "generic/centos8"
        docker_node3.vm.synced_folder ".", "/home/vagrant/host"
        docker_node3.vm.synced_folder ".", "/vagrant", disabled: true
        docker_node3.vm.provider "virtualbox" do |v|
          v.memory = 1024
        end

        docker_node3.vm.provision "shell", inline: $change_sshd_config, privileged: false

        docker_node3.trigger.after :up do |trigger|
          trigger.warn = "Docker node online!"
        end
        docker_node3.vm.network "private_network", ip: "172.17.167.15"
        docker_node3.vm.hostname = 'centos-docker-3.local'
    end
    
    
    # --------------------------------------------------------------------------------------------------------------------------------------------
    config.vm.define 'docker-4', autostart: false do |docker_node4|
        docker_node4.vm.box = "generic/centos8"
        docker_node4.vm.synced_folder ".", "/home/vagrant/host"
        docker_node4.vm.synced_folder ".", "/vagrant", disabled: true
        docker_node4.vm.provider "virtualbox" do |v|
          v.memory = 1024
        end

        docker_node4.vm.provision "shell", inline: $change_sshd_config, privileged: false

        docker_node4.trigger.after :up do |trigger|
          trigger.warn = "Docker node online!"
        end
        docker_node4.vm.network "private_network", ip: "172.17.167.16"
        docker_node4.vm.hostname = 'centos-docker-4.local'
    end
end