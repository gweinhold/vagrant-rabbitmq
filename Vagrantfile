# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.hostname = "rabbitmq-vm"
  config.vm.box = "ubuntu/trusty32"
  config.vm.network :forwarded_port, guest: 5672, host: 5672
  config.vm.network :forwarded_port, guest: 15672, host: 15672

  config.vm.provision "shell", inline: <<-SHELL
    echo "deb http://www.rabbitmq.com/debian/ testing main" > /etc/apt/sources.list.d/rabbitmq.list

    wget http://www.rabbitmq.com/rabbitmq-signing-key-public.asc
    apt-key add rabbitmq-signing-key-public.asc

    apt-get -qq update
    apt-get -qq install -y rabbitmq-server

    rabbitmq-plugins enable rabbitmq_management
    #Allows for guest login access from non localhost users.  Disabled by default in RabbitMQ 3.3.0
    echo "[{rabbit, [{loopback_users, []}]}]." > /etc/rabbitmq/rabbitmq.config
    service rabbitmq-server stop
    service rabbitmq-server start
  SHELL
  
  config.vm.provider :virtualbox do |v|
    v.name = "rabbitmq-vm"
  end

end
