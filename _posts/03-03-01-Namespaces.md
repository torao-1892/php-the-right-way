---
title: Namespaces
isChild: true
anchor: namespaces
---

## Namespaces {#namespaces_title}

Como mencionado anteriormente, a comunidade PHP tem muitos desenvolvedores criando muito código. Isso significa que o
código de uma biblioteca PHP pode usar o mesmo nome de classe que uma outra biblioteca. Quando ambas bibliotecas são
usadas no mesmo namespace, elas colidem e causam problemas.

Os _Namespaces_ resolvem esse problema. Como descrito no manual de referência do PHP, os namespaces podem ser
comparados com os diretórios dos sistemas operacionais, que fazem _namespace_ dos arquivos; dois arquivos com o mesmo
nome podem coexistir em diretórios separados. Da mesma forma, duas classes PHP com o mesmo nome podem coexistir em
namespaces PHP separados. Simples assim.

É importante que você use namespace no seu código para que ele possa ser usado por outros desenvolvedores sem risco
de colisão com outras bibliotecas.

Um modo recomendado de usar namespaces está descrito na [PSR-0][psr0], que tem como objetivo fornecer uma convenção
padrão para arquivos, classes e namespaces, permitindo código plug-and-play.

Em dezembro de 2013 o PHP-FIG (Grupo de Interoperabilidade entre Frameworks) criou um novo padrão para carregamento automático, a [PSR-4][psr4], que provavelmente vai substituir a PSR-0. Atualmente ambos são utilizáveis, pois a PSR-4 requer o PHP 5.3 e muitos projetos que usam apenas o PHP 5.2 ainda implementam a PSR-0. Se você for usar um padrão de carregamento automático para uma nova aplicação ou pacote então é quase certo que você vai querer olhar para a PSR-4.

```
Nota do tradutor
* Aguardando atualização do repositório oficial sobre o uso da PSR-0 que foi 
marcada como deprecada em 21/10/2014. 
```

* [Leia sobre os Namespaces][namespaces]
* [Leia sobre a PSR-0][psr0]
* [Leia sobre a PSR-4][psr4]

[namespaces]: http://php.net/manual/en/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md