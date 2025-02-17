Vagrant.configure("2") do |config|
  config.vm.box = "debian/bullseye64"
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "256"
  end
  
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update && apt-get install -y nginx
  SHELL
  
  config.vm.define "proxy" do |proxy|
    proxy.vm.hostname = "www.example.test"
    proxy.vm.network "private_network",ip: "192.168.57.10"
  end
  
  config.vm.define "web" do |web|
    web.vm.hostname = "w1.example.test"
    web.vm.network "private_network",ip: "192.168.57.11"
  end  
end