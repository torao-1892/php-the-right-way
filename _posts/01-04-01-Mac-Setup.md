---
title: Instalação no Mac
isChild: true
anchor: instalacao_no_mac
---

## Instalação no Mac {#instalacao_no_mac_title}

O OS X já vem com o PHP, mas ele é normalmente um pouco atrasado em relação à última versão estável. O Mountain Lion 
vem com a 5.3.10, o Mavericks com a 5.4.17 e o Yosemite com a 5.5.9.

Existem várias maneiras de instalar o PHP no Mac OS X.

[Homebrew](http://brew.sh/) é um poderoso gerenciador de pacotes para OS X, que pode ajudá-lo a instalar o PHP e várias 
extensões facilmente. [Homebrew PHP] é um repositório que contém "fórmulas" relacionadas ao PHP para Homebrew e permite 
a você instalar o PHP.

Neste ponto, você pode instalar o `php53`, `php54`, `php55` ou `php56` usando o comando `brew install` e alternar entre 
elas modificando a variável `PATH`.

### Instalar PHP via phpbrew

[phpbrew] é uma ferramenta para instalar e gerenciar múltiplas versões do PHP. Isto pode ser realmente útil se duas 
diferentes aplicações/projetos requerem diferentes versões do PHP e você não está usando máquinas virtuais.

### Compilar o código fonte

Outra opção que lhe dá o controle sobre a versão do PHP você instalar, é [compilar o código fonte][mac-compile].
Nesse caso, certifique-se de ter instalado o XCode ou o substituto da Apple ["Command Line Tools for XCode"] que pode 
ser encontrado no _Apple's Mac Developer Center_.

### Instaladores _All-in-One_

As soluções listadas acima lidam apenas com o PHP e não fornecem coisas como Apache, Nginx ou um servidor SQL. As 
soluções _All-in-one_ como [MAMP][mamp-downloads] e [XAMPP][xampp] vão instalar estes outros programas para você e 
amarrá-los todos juntos, mas a facilidade de configuração vem com o contra-ponto da flexibilidade.

[Homebrew]: http://brew.sh/
[Homebrew PHP]: https://github.com/Homebrew/homebrew-php#installation
[mac-compile]: http://www.php.net/manual/en/install.macosx.compile.php
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
["Command Line Tools for XCode"]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/
[phpbrew]: https://github.com/phpbrew/phpbrew
[xampp]: http://www.apachefriends.org/en/xampp.html