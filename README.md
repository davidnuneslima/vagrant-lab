# Vagrant_Server_01

Criando uma única instância com o Vagrant.

Distribuição linux utilizada FEDORA 34.

VirtualBox 6.1

    1. Instalação do Virtualbox
 
    • Adicionar VirtualBox RPM repository:
 
      sudo dnf -y install wget wget http://download.virtualbox.org/virtualbox/rpm/fedora/virtualbox.repo sudo mv virtualbox.repo /etc/yum.repos.d/virtualbox.repo

    • Adicionando repositórios:

      sudo dnf install -y gcc binutils make glibc-devel patch libgomp glibc-headers kernel-headers kernel-devel-uname -r dkms

    • Instalando VirtuallBox:

      sudo dnf install VirtualBox-6.1

    • Adicionar usuário ao grupo vboxusersgroup:

      sudo usermod -a -G vboxusers NOMEDOUSUARIO

    • Configurando Drivers VirtualBox: 

      sudo /usr/lib/virtualbox/vboxdrv.sh setup

    • Instalando Extension Pack: 

      cd ~/ wget https://download.virtualbox.org/virtualbox/6.1.22/Oracle_VM_VirtualBox_Extension_Pack-6.1.22.vbox-extpack 

    2. Instalação do Vagrant 

      sudo dnf -y install vagrant

    3. Criando a instância no Vagrant 

    • Criar e acessar o diretório

      mkdir ~/vagrant_01/ cd ~/vagrant_01/

    • Iniciando o vagrant com a box fedora34

      vagrant init -m fedora/34-cloud-base

    • Editando o Vagrantfile com o editor VIM

      vim Vagrantfile

      Vagrant.configure("2") do |config| 

      config.vm.box = "fedora/34-cloud-base" 

      config.vm.provider "virtualbox" do |vb| 

      vb.memory = "1024" 

      vb.cpus = "2" 

      end 
end

    • vagrant up (Esse comando irá iniciar a instância no VirtualBox).

    • vagrant ssh (Esse comando irá acessar a instância via terminal).

    • vagrant halt (Esse comando irá desligar a instância no VirtualBox).

    • vagrant destroy (Esse comando irá destruir a instância no VirtualBox).
