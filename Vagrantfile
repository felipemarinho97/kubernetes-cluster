IMAGE_NAME = "ubuntu/xenial64"
NODES = 2

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.provider "virtualbox" do |vb|
        vb.memory = 2048
        vb.cpus = 2
    end

    # Create the master node
    config.vm.define "k8s-master" do |master|
        master.vm.box = IMAGE_NAME
        master.vm.hostname = "k8s-master"
        master.vm.network "private_network", ip: "10.0.0.10"
        master.vm.provision "ansible" do |ansible|
            ansible.playbook = "kubernetes-setup/master-playbook.yml"
            ansible.extra_vars = {
                node_ip: "10.0.0.10",
            }
        end
    end

    # Create the worker nodes
    (1..NODES).each do |i|
        config.vm.define "node-#{i}" do |node|
            node.vm.box = IMAGE_NAME
            node.vm.hostname = "node-#{i}"
            node.vm.network "private_network", ip: "10.0.0.#{i + 10}"
            node.vm.provision "ansible" do |ansible|
                ansible.playbook = "kubernetes-setup/node-playbook.yml"
                ansible.extra_vars = {
                    node_ip: "10.0.0.#{i + 10}",
                }
            end
        end
    end
end

