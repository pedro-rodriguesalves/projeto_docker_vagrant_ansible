# Projeto DevOps com Docker, Vagrant e Ansible 

**AUTORIDADES MÁXIMAS:** Pedro Henrique Rodrigues Alves - (20241380026) e Felipe da Silva Oliveira - (20241380003).

**DISCIPLINA:** Administração de Sistemas Abertos.

**PROFESSOR, ORIENTADOR E AUTORIDADE MÁXIMA:** Leonidas Francisco de Lima Júnior.

## Introdução

<p align="justify">
Este projeto tem como objetivo automatizar o provisionamento e a configuração de um ambiente virtual baseado em Debian Linux, utilizando Vagrant e Ansible, integrando conceitos de DevOps. A infraestrutura utiliza Docker e Docker Compose para disponibilizar uma aplicação WordPress com banco de dados MySQL, além de um proxy Nginx responsável pelo encaminhamento das requisições. Todos os arquivos de configuração e a documentação necessária estão organizados neste repositório, possibilitando a reprodução, o estudo e a manutenção do ambiente de forma simples e padronizada.
</p>

## Vagrantfile:

O projeto inclui um Vagrantfile que define a criação de uma máquina virtual:

- Provider: VirtualBox;
- Box: debian/bookworm64;
- Versão da API do Vagrant: 2;
- Geração automática de chaves SSH: desabilitada;
- Plugin vagrant-vbguest: atualização automática desabilitada (quando presente);
- Tipo de rede: rede privada (private_network);
- Endereço IP: 192.168.56.163;
- Hostname: pedro.felipe;
- Memória RAM: 1024 MB;
- Interface gráfica (GUI): desabilitada (headless);
- Nome da máquina virtual no VirtualBox: definido conforme o hostname;
- Verificação de Guest Additions: desabilitada;
- Provisionamento automático: realizado com Ansible;
- Playbook utilizado: playbook_ansible.yml;
- Modo de compatibilidade do Ansible: 2.0.

## playbook_ansible.yml:

- Atualização da lista de pacotes do sistema;
- Atualização dos pacotes instalados (upgrade dist);
- Instalação de dependências básicas para repositórios HTTPS;
- Adição da chave GPG oficial do Docker;
- Adição do repositório oficial do Docker para Debian Bookworm;
- Instalação do Docker Engine e do Docker Compose v2;
- Inicialização e habilitação do serviço Docker na inicialização do sistema;
- Adição do usuário vagrant ao grupo docker;
- Criação do diretório do projeto em /opt/wordpress;
- Cópia do arquivo docker-compose.yml para a máquina virtual;
- Inicialização dos contêineres Docker utilizando Docker Compose.


## docker-compose.yml: 

- Nome do projeto: projeto-pf;
- Serviço webproxy:
     - Imagem Docker personalizada hospedada no Docker Hub;
     - Exposição da porta 8080;
     - Dependência do serviço Wordpress;
- Serviço webserver (WordPress):
     - Imagem oficial wordpress:latest;
     - Persistência de dados via volume Docker;
     - Configuração de variáveis de ambiente para conexão com o banco de dados;
- Serviço database (MySQL):
     - Imagem oficial mysql:8.0;
     - Persistência de dados via volume Docker;
     - Configuração automática do banco, usuário e credenciais;
- Utilização de volumes persistentes para dados do Wordpress e do MySQL;
- Comunicação entre os serviços através de uma rede bridge dedicada.

## Dockerfile:

- Utilização da imagem base nginx:latest;
- Instalação de ferramentas de diagnóstico de rede (ping e curl);
- Remoção de arquivos temporários para otimização do tamanho da imagem;
- Cópia de um arquivo de configuração personalizado do Nginx;
- Exposição da porta 8080 para acesso externo ao proxy.

## nginx.conf:

- Definição de um único processo de trabalho do Nginx;
- Configuração de eventos com limite de conexões simultâneas;
- Utilização do módulo stream para proxy TCP;
- Definição de um upstream apontando para o serviço Wordpress;
- Escuta de conexões na porta 8080;
- Encaminhamento do tráfego recebido para o servidor backend.


## Execução do Projeto:

### **Pré-requisitos**
- **VirtualBox** Instalado.  
- **Vagrant** Instalado.  
- **Ansible** Instalado.
- **Docker** Instalado.  
  

### **Passos Necessários para a execução:**

1. **Clone este repositório:**
   ```bash
   git clone https://github.com/pedro-rodriguesalves/projeto_vagrant_ansible.git
   cd projeto_vagrant_ansible
   
2. **Suba as VMs:**
   ```bash
   vagrant up 

