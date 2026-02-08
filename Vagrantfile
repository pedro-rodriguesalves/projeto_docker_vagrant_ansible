# -*- mode: ruby -*-
# vi: set ft=ruby :

# Definindo a versão de configuração do Vagrant.
Vagrant.configure("2") do |config|

  # Definindo a box como "debian/bookworm64".
  config.vm.box = "debian/bookworm64"

  # Impede que o Vagrant gere novas chaves SSH.
  config.ssh.insert_key = false

  # Configuração do plugin vagrant-vbguest (adiciona suporte a guest additions).
  if Vagrant.has_plugin?("vagrant-vbguest")
    # Desativa atualização automática do guest additions.
    config.vbguest.auto_update = false
  end

  # Definindo o hostname.
  config.vm.hostname = "pedro.felipe"

  # Definindo a rede privada com ip: 192.168.56.163 .
  config.vm.network "private_network", ip: "192.168.56.163"

  # Configurações específicas do provedor VirtualBox:
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"                  # Memória RAM.
    vb.gui = false                      # Desabilitando GUI (Interface Gráfica).
    vb.name = config.vm.hostname        # Definindo o nome da máquina virtual.
    vb.check_guest_additions = false    # Desabilita verificação de guest additions.
  end

  # Provisionamento do Ansible.
  config.vm.provision "ansible" do |ansible|

    # Definindo o modo de compatibilidade do Ansible.
    ansible.compatibility_mode = "2.0"

    # Define o playbook que será  utilizado durante o provisionamento.
    ansible.playbook = "playbook_ansible.yml"
  end
end
