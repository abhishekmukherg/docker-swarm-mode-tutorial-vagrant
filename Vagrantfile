# -*- mode: ruby -*-
# vi: set ft=ruby :

$num_workers = 2
$num_managers = 1
$num_nodes = $num_workers + $num_managers
$vm_cpus = 2
$vm_mem = 2048
$manager_ip = "192.168.99.100"
$worker_ip_base = "192.168.99."
$node_ips = $num_nodes.times.collect { |n| $worker_ip_base + "#{n+101}" }

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  def customize_vm(config)
    config.vm.provider "virtualbox" do |vb|
      # Customize the amount of memory on the VM:
      vb.memory = $vm_mem
      vb.cpus = $vm_cpus
    end
  end

  $num_managers.times do |n|
    config.vm.define "manager#{n+1}" do |node|
      customize_vm node
      manager_ip = $manager_ip
      node.vm.network "private_network", ip: "#{manager_ip}"
      node.vm.hostname = "manager#{n+1}"
    end
  end

  $num_workers.times do |n|
    config.vm.define "worker#{n+1}" do |node|
      customize_vm node
      node_ip = $node_ips[n]
      manager_ip = $manager_ip
      node.vm.network "private_network", ip: "#{node_ip}"
      node.vm.hostname = "worker#{n+1}"
      if n == $num_workers - 1
        node.vm.provision "ansible" do |ansible|
          ansible.limit = "all"
          ansible.playbook = "install_docker.yml"
        end
      end
    end
  end
end
