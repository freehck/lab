IMAGE_NAME = "geerlingguy/ubuntu1804"
N = 3
CIDR_PREFIX = "10.118.19."  # because k=11 and s=19, therefore k8s=118.19 :)

Vagrant.configure("2") do |config|
  vagrant_root = File.dirname(__FILE__)
  ENV['ANSIBLE_ROLES_PATH'] = "#{vagrant_root}/roles"

  config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |v|
    #v.memory = 2048
    v.memory = 3072
    v.cpus = 2
  end

  (0..N).each do |i|
    config.vm.define "k8s-node-#{i}" do |node|
      node.vm.box = IMAGE_NAME
      node.vm.network "private_network", ip: CIDR_PREFIX+"#{10+i}"
      node.vm.hostname = "k8s-node-#{i}"
    end
  end
end
