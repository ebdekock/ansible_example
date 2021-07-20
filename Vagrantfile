servers=[
  {
    :hostname => "web1",
    :ip => "10.1.0.10",
    :box => "bento/ubuntu-18.04",
    :ram => 512,
    :cpu => 2
  },
  {
    :hostname => "web2",
    :ip => "10.1.0.11",
    :box => "bento/ubuntu-18.04",
    :ram => 512,
    :cpu => 2
  },
  {
    :hostname => "mysql",
    :ip => "10.1.0.12",
    :box => "bento/ubuntu-18.04",
    :ram => 512,
    :cpu => 2
  },
  {
    :hostname => "psql",
    :ip => "10.1.0.13",
    :box => "bento/ubuntu-18.04",
    :ram => 512,
    :cpu => 2
  }
]

Vagrant.configure(2) do |config|
  servers.each do |machine|
      config.vm.define machine[:hostname] do |node|
          node.vm.box = machine[:box]
          node.vm.hostname = machine[:hostname]
          node.vm.network "private_network", ip: machine[:ip]
          node.vm.provider "virtualbox" do |vb|
              vb.customize ["modifyvm", :id, "--memory", machine[:ram]]
          end
      end
      config.vm.provision "shell" do |s|
        ssh_pub_key = File.readlines("#{Dir.home}/.ssh/vagrant_key.pub").first.strip
        s.inline = <<-SHELL
          echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
        SHELL
      end
  end
end
