Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  
  # Changed IP to avoid .1 conflict
  config.vm.network "private_network", ip: "192.168.33.10"
  
  # Jenkins port forwarding
  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4000"
    vb.cpus = "2"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y openjdk-17-jdk
    wget https://pkg.jenkins.io/debian-stable/binary/jenkins_2.401.3_all.deb
    sudo dpkg -i jenkins_2.401.3_all.deb
    sudo apt-get install -f -y
    sudo systemctl start jenkins
  SHELL
end