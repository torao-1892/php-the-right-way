---
title: Composer e Packagist
isChild: true
---

## Composer e Packagist {#composer_e_packagist_title}

O Composer é um gerenciador de dependências **brilhante** para o PHP. Liste as dependências do seu projeto em um
arquivo `composer.json` e, com poucos comandos simples, o Composer irá fazer o download das dependências do seu
projeto automaticamente e configurará o autoloading para você.

Já existem várias bibliotecas PHP que são compatíveis com o Composer, prontas para usar no seu projeto. Esses "pacotes"
estão listados no [Packagist][1], o repositório oficial das bibliotecas PHP compatíveis com o Composer.

### Como Instalar o Composer

Você pode instalar o Composer localmente (no seu diretório de trabalho atual; embora isso não seja mais recomendado)
ou globalmente (e.g. /usr/local/bin). Vamos assumir que você queira instalar o Composer localmente. A partir do
diretório raiz do seu projeto:

    curl -s http://getcomposer.org/installer | php

Isso irá baixar o `composer.phar` (um arquivo PHP binário). Você pode executá-lo com o `php` para gerenciar as
dependências do seu projeto. <strong>Por favor, Observe:</strong> Se você passar o código baixado diretamente para um
interpretador, por favor leia primeiro o código online para confirmar que ele é seguro.

### Como instalar o Composer (manualmente)

Instalar o Composer manualmente é uma técnica avançada; no entanto, existem várias razões pelas quais um
desenvolvedor poderia preferir esse método a usar a rotina de instalação interativa. A instalação interativa verifica
sua instalação do PHP para garantir que:

- uma versão suficiente do PHP esteja sendo usada
- arquivos `.phar` possam ser executados corretamente
- permissões em certos diretórios sejam suficientes
- certas extensões problemáticas não estejam carregadas
- certas configurações no `php.ini` não estejam definidas

Como uma instalação manual não executa nenhuma dessas verificações, você precisa decidir se o custo valerá a pena
para você. Se sim, segue abaixo como obter o Composer manualmente:

    curl -s http://getcomposer.org/composer.phar -o $HOME/local/bin/composer
    chmod +x $HOME/local/bin/composer

O caminho `$HOME/local/bin` (ou um diretório de sua escolha) deve estar na sua variável de ambiente `$PATH`. Isso
fará com que o comando `composer` fique disponível.

Quando você vir a documentação dizendo para executar o Composer como `php composer.phar install`, você pode
substituir por isso:

    composer install

### Como Definir e Instalar Dependências

Primeiramente, crie um arquivo `composer.json` no mesmo diretório do `composer.phar`. Aqui está um exemplo que lista
o [Twig][2] como uma dependência do projeto.
O Composer mantém o controle de dependências do seu projeto em um arquivo chamado `composer.json`. Você pode
controlá-lo na mão se preferir ou usar o próprio Composer. O comando `php composer.phar require` adiciona um
dependência do projeto e se você não tem um arquivo `composer.json`, ele será criado. Aqui está um exemplo que adiciona
o [Twig][2] como uma dependência do seu projeto. Execute no diretório raiz do seu projeto onde baixou o
`composer.phar`:

    {
        "require": {
            "twig/twig": "1.8.*"
        }
    }

Outra alternativa é o comando `php composer.phar init` que guiará a criação completa do arquivo `composer.json` para
seu projeto. De qualquer maneira, uma vez criado o arquivo `composer.json` você pode chamar o Composer para baixar suas
dependências para o diretório `vendors/`. Isto também se aplica para projetos baixados que fornecem um arquivo
`composer.json`:

    php composer.phar install

Em seguida, adicione esta linha ao arquivo PHP principal da sua aplicação; isso dirá ao PHP para usar o autoloader do
Composer para as dependências do seu projeto.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Agora você pode usar as dependências do seu projeto, e elas serão carregadas automaticamente sob demanda.

### Atualizando suas dependências

O Composer cria um arquivo chamado `composer.lock` que armazena a versão exata de cada pacote baixado quando você
executou `php composer.phar install`. Se você compartilhar seu projeto com outros desenvolvedores e o arquivo
`composer.lock` é parte da sua distribuição, quando eles executarem `php composer.phar install` receberão as mesmas
versões como você.
Para atualizar suas dependências, execute `php composer.phar update`.
Isso é muito útil quando você define as versões requiridas. Por exemplo, a versão requerida de ~1.8 significa "qualquer
coisa mais recente que 1.8.0, mas menos do que 2.0.x-dev". Você também pode usar o `*` curinga como `1.8.*`. Agora
o comando `php composer.phar update` do Composer atualizará todas as suas dependências para a versão mais recente que
se encaixa às restrições definidas.

### Verificando suas dependências para as questões de segurança

O [Security Advisories Checker][3] é um serviço web e uma ferramenta de linha de comando, ambos examinarão seu arquivo
`composer.lock` e diz se você precisa atualizar alguma das dependências.

* [Aprenda sobre o Composer][4]

[1]: http://packagist.org/
[2]: http://twig.sensiolabs.org
[3]: https://security.sensiolabs.org/
[4]: http://getcomposer.org/doc/00-intro.md