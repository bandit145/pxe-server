Vagrant.configure("2") do |config|

        (1..1).each do |i|

            config.vm.define "server#{i}" do |client|
   				client.vm.provider "virtualbox" do |vm|
					vm.memory = 4096
				end
            	client.vm.box = "bento/centos-7.4"
                config.vm.provision "shell", inline: "yum -y install epel-release"
                config.vm.provision "shell", inline: "yum -y install python-pip"
                config.vm.provision "shell", inline: "pip install ansible"
                config.vm.provision "ansible_local" do |ansible|
                    ansible.playbook = "pxe.yml"
                end
            	client.vm.network "private_network", ip: "192.168.50.#{i+1}"
            	client.vm.synced_folder "E:/github/", "/git"
            end
        end

end

