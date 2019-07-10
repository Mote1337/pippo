Vagrant.configure("2") do |config|
	config.vm.box = "centos/7"

	config.vm.define :pippo do |pippo_config|
		pippo_config.vm.provider :virtualbox do |vb_config|
      #Assegnazione nome su Virtual Box
      vb_config.name = "Pippo the Jenkin DogMan"
      end
      #Hostname della macchina, la sintassi è pippo_config, definita nel vm.define, .vm ((virtual machine)) e opzione hostname
    pippo_config.vm.hostname = "pippo.disney"
      #Creazione di una network privata con assegnazione dell'IP
      pippo_config.vm.network "private_network",
        ip: "192.168.10.20"
      #Messaggio a schermata dopo vagrant up
      pippo_config.vm.post_up_message = "PIPPUP!"
      #Cartella sharata per avere il file di ansible editabile dal mio mac!
      pippo_config.vm.synced_folder "share_nfs/", "/share/",
        create: true,
        type: "nfs",
        mount_options: ["actimeo=2"]
      #Parte di gestione ansible
      pippo_config.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "provision/playbook.yml"
        end
      end
end

#config.vm.network "forwarded_port", guest: 80, host: 8086
#  config.vm.network "forwarded_port", guest: 22, host: 2050
