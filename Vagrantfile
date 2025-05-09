Vagrant.configure("2") do |config|
  
  # Базовый образ для обоих ВМ
  config.vm.box = "centos/8"

  # Общий пакет через NFS
  config.vm.synced_folder "./shared", "/vagrant_shared", type: "nfs", nfs_version: 4

  # Конфигурация первой ВМ
  config.vm.define "vm1" do |vm1|
    vm1.vm.hostname = "vm1"
    vm1.vm.network "private_network", ip: "192.168.56.101"
    vm1.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
    vm1.vm.provision "file", source: "shared/example.txt", destination: "/home/vagrant/example.txt"
  end

  # Конфигурация второй ВМ
  config.vm.define "vm2" do |vm2|
    vm2.vm.hostname = "vm2"
    vm2.vm.network "private_network", ip: "192.168.56.102"
    vm2.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
    vm2.vm.provision "file", source: "shared/example.txt", destination: "/home/vagrant/example.txt"
  end
end

