# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
#--- INICIO MAQUINA DEL WEB SERVER ---
  #Configurar para iniciar ssh de servidor usando: vagrant ssh web 
  config.vm.define "web" do |web|
    web.vm.box = "centos/7"
    web.vm.network "private_network", ip: "192.168.0.10"
    web.vm.provision "shell", inline: <<-SHELL
      echo "webserver" > /etc/hostname
      #Confiugrar hostname del servidor
      hostname -b webserver
      #Haciendo que webserver pueda enconctrar al clockserver por nombre
      echo "192.168.0.20        clockserver" >> /etc/hosts
    SHELL
  end  
#--- INICIO MAQUINA DEL SERVER DE LA HORA ---
  #Configurar para iniciar ssh de servidor usando: vagrant ssh clock
  config.vm.define "clock" do |clock|
    clock.vm.box = "centos/7"
    clock.vm.network "private_network", ip: "192.168.0.20"
    clock.vm.provision "shell", inline: <<-SHELL
      echo "clockserver" > /etc/hostname
      #Confiugrar hostname del servidor
      hostname -b clockserver
      #Haciendo que clockserver pueda enconctrar al webserver por nombre
      echo "192.168.0.10        webserver" >> /etc/hosts
    SHELL
  end  
end