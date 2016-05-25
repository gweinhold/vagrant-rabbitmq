# vagrant-rabbitmq
Simple Vagrantfile for setting up RabbitMQ and the management plugin.  Forwards localhost:5672 and localhost:15672 to the vm.

Requires Vagrant installed
https://www.vagrantup.com/docs/installation/

### Getting setup

    git clone https://github.com/gweinhold/vagrant-rabbitmq.git
    cd vagrant-rabbitmq
    vagrant up

Open browser to http://localhost:15672 (guest/guest)

AMQP is up and running at http://localhost:5672