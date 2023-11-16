Vagrant.configure("2") do |config|
  # Define the first node ; change
  config.vm.define "node1" do |node1|
    node1.vm.box = "bento/centos-7"
    node1.vm.network "public_network", bridge: "Беспроводная сеть", ip: "192.168.88.101"
    node1.vm.hostname = "node1"
    node1.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
    node1.vm.provision "shell", inline: <<-SHELL
      useradd -m -s /bin/bash percona
    SHELL
  end

  # Define the second node
  config.vm.define "node2" do |node2|
    node2.vm.box = "centos/7"
    node2.vm.network "public_network", bridge: "Беспроводная сеть", ip: "192.168.88.102"
    node2.vm.hostname = "node2"
    node2.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
    node2.vm.provision "shell", inline: <<-SHELL
      useradd -m -s /bin/bash percona
    SHELL
  end

  # Define the third node with MySQL
  config.vm.define "node3" do |node3|
    node3.vm.box = "centos/7"
    node3.vm.network "public_network", bridge: "Беспроводная сеть", ip: "192.168.88.103"
    node3.vm.hostname = "node3"
    node3.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    node3.vm.provision "shell", inline: <<-SHELL
      useradd -m -s /bin/bash percona
      yum install -y https://repo.percona.com/yum/percona-release-latest.noarch.rpm
      yum install -y Percona-Server-server-57
      systemctl start mysqld
      systemctl enable mysqld
    SHELL
  end
end
