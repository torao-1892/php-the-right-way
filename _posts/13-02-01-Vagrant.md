---
title: Vagrant
isChild: true
anchor: vagrant
---

## Vagrant {#vagrant_title}

O [Vagrant][vagrant] ajuda a construir suas máquinas virtuais em cima de ambientes virtuais conhecidos e a configurar esses ambientes com base em um único arquivo de configuração.
As máquinas
virtuais base (box) podem ser configuradas manualmente, ou você pode usar um software de "provisionamento" como o
[Puppet][puppet] ou o [Chef][chef] para fazer isso por você. Provisionar o box é uma ótima maneira de garantir que
as múltiplas máquinas virtuais sejam configuradas de forma idêntica e que você não necessite manter complicadas
listas de comandos de configuração. Você pode também destruir (destroy) o box base e recriá-lo sem muitos passos
manuais, tornando fácil criar instalações novas.

O Vagrant cria pastas compartilhadas para compartilhar seu código entre sua máquina e a máquina virtual, assim você
pode criar e editar seus arquivos na sua máquina e então executar seu código dentro da máquina virtual.

### Uma pequena ajuda

Se você precisa de uma pequena ajuda para inciar o uso do Vagrant existem dois serviços que podem ser úteis:
- [Rove][rove]: serviço que permite que você gere configurações típicas do Vagrant, sendo o PHP uma das opções. O provisionamento é realizado com Chef.
- [Puphpet][puphpet]: GUI simples de configurar máquinas virtuais para o desenvolvimento PHP. ** Altamente focada em PHP **. Além VMs local, ele pode ser usado para implantar em serviços de nuvem também. O provisionamento é feito com Puppet.
- [Protobox][protobox]: é uma camada em cima do vagrant e uma interface gráfica web para configuração de máquinas virtuais para o desenvolvimento web. Um único documento YAML controla tudo o que está instalado na máquina virtual.
- [Phansible][phansible]: oferece uma interface que ajuda a gerar Ansible Playbooks para projetos baseados em PHP.

[vagrant]: http://vagrantup.com/
[puppet]: http://www.puppetlabs.com/
[chef]: http://www.opscode.com/
[rove]: http://rove.io/
[puphpet]: https://puphpet.com/
[protobox]: http://getprotobox.com/
[phansible]: http://phansible.com/
