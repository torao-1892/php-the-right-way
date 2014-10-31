# Contribuir com o projeto utilizando o Vagrant

### Instalar o vagrant
* Instale [Vagrant](http://www.vagrantup.com/) e [VirtualBox](https://www.virtualbox.org/)
* Execute o comando `vagrant up` no diretório do projeto

### Gerar o build do projeto e visualizar localmente
* Realize as alterações
* Para criar o build:
  * Execute `vagrant ssh -c 'cd /vagrant && jekyll build'`
* Para visualizar as alterações:
  * Execute `vagrant ssh -c 'cd /vagrant && jekyll serve'`
  * Acesse [visualize localmente](http://localhost:4000)