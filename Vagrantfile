# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
	#BOXES
	config.vm.box = "centos/7"
	
	#NETWORKING
	#Forwarding ports
	#config.vm.network :forwarded_port, guest: 5602, host: 5602
	#config.vm.network :forwarded_port, guest: 9200, host: 9202
	#config.vm.network :forwarded_port, guest: 9302, host: 9302
	#config.vm.network :forwarded_port, guest: 8080, host: 8080

	config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
	
	#Customizing machine
    config.vm.provider "virtualbox" do |vb|
		vb.name = "centos-elk"
		vb.memory = 2048
		vb.cpus = 2
	end

	#**********SYNCED FOLDERS*************
	# Configuración para evitar error de GuestAditions. The first argument is the path on the host to the actual folder. The second argument is the path on the guest to mount the folder
	config.vm.synced_folder "./", "/vagrant", type: "virtualbox"
	
	# PROVISIONING
	# OPCION 1 - SHELL PROVISIONING - FLEXIBLE PERO COMPLEJO Y ATADO A LA DISTRIBUCION LINUX
	#config.vm.provision :shell, :keep_color => true, :path => "setup.sh"

	# OPCION 2 - DOCKER PROVISIONER
	config.vm.provision "docker" do |d|
		#d.pull_images "nginx"
		#d.pull_images "elasticsearch"
		#d.pull_images "docker.elastic.co/elasticsearch/elasticsearch:5.4.1"
		#d.run "docker.elastic.co/elasticsearch -p 9200:9200 -e http.host=0.0.0.0 -e transport.host=127.0.0.1 docker.elastic.co/elasticsearch/elasticsearch:5.4.1 /bin/bash"

		#d.pull_images "docker.elastic.co/logstash/logstash:5.4.1"
		#d.run --rm -it -v ~/pipeline/:/usr/share/logstash/pipeline/ docker.elastic.co/logstash/logstash:5.4.1

		#d.pull_images "docker.elastic.co/kibana/kibana:5.4.1"
		#docker run --name nginx-prueba -d -p 8080:80 some-content-nginx
    end	

end
