# Projeto DevOps com Vagrant e Ansible

**AUTORIDADES MÁXIMAS:** Pedro Henrique Rodrigues Alves - (20241380026) e Felipe da Silva Oliveira - (20241380003).

**DISCIPLINA:** Administração de Sistemas Abertos.

**PROFESSOR, ORIENTADOR E AUTORIDADE MÁXIMA:** Leonidas Francisco de Lima Júnior.

## Introdução

<p align="justify">
Este projeto tem como objetivo automatizar o provisionamento e a configuração de uma infraestrutura composta por quatro máquinas virtuais Linux (Debian), utilizando Vagrant e Ansible. O ambiente simula um cenário real de DevOps, integrando serviços como SSH, NFS, LVM, DHCP, Apache, MariaDB e um servidor DNS para resolução interna de nomes. Toda a documentação, bem como o Vagrantfile e os playbooks Ansible, está organizada neste repositório para facilitar reprodução e manutenção do ambiente.
</p>

## Vagrantfile

O projeto inclui um Vagrantfile que define a criação de uma máquina virtual:

- Provider: VirtualBox;
- Box: debian/bookworm64
- Geração de chaves SSH desabilitada;
- IP: 192.168.56.163;
- Hostname: pedro.felipe
- Memória RAM: 1024 MB;
- Verificação de guest additions desabilitado.

## playbook_ansible.yml

- Atualização do Sistema Operacional.
- Instalação do Docker e Docker-compose 2;



## docker-compose.yml 

- Criação de Containers.
- Criação de Volumes.




## Execução do Projeto:

### **Pré-requisitos**
- **VirtualBox** Instalado.  
- **Vagrant** Instalado.  
- **Ansible** Instalado no Host.  
  

### **Passos Necessários para a execução:**

1. **Clone este repositório:**
   ```bash
   git clone https://github.com/pedro-rodriguesalves/projeto_vagrant_ansible.git
   CD projeto_vagrant_ansible
   
2. **Suba as VMs:**
   ```bash
   vagrant up 

