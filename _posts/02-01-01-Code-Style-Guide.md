# Guia de estilo de código

A comunidade PHP é grande e diversa, composta por inúmeras bibliotecas, frameworks e componentes. É comum para desenvolvedores PHP escolher vários destes e combiná-los em um único projeto. É importante que código PHP siga um estilo de código comum para que desenvolvedores PHP possam misturar várias bibliotecas em seus projetos.

O [Framework Interop Group][fig] (outrora conhecido como 'PHP Standards Group') propôs e aprovou várias recomendações de estilo, conhecidas como
[PSR-0][psr0], [PSR-1][psr1] e [PSR-2][psr2]. Não deixe os nomes estranhos confundi-lo, estas recomendações são meramente um conjunto de regras que projetos como Drupal, Zend, CakePHP, phpBB, AWS SDK, FuelPHP, Lithium, etc estão começando a adotar. Você pode utilizá-las para seus próprios projetos, ou continuar utilizando seu estilo pessoal.

Idealmente você deveria escrever código PHP que adere a um ou mais destes padrões, de forma que outros desenvolvedores possam facilmente ler e trabalhar no seu código. Estes padrões são cumulativos, portanto usar PSR-1 requere a PSR-0, mas não requere a PSR-2.

* [Leia sobre a PSR-0][psr0]
* [Leia sobre a PSR-1][psr1]
* [Leia sobre a PSR-2][psr2]

Você pode usar o sniff [phpcs-psr][phpcs-psr] para o [PHP_CodeSniffer][phpcs] para checar seu código para as recomendações. Use o 
[PHP Coding Standards Fixer][phpcsfixer] do Fabien Potencier para automaticamente modificar seu código para que ele seja compatível com os padrões, evitando precisar fazer as alterações na mão.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[phpcs-psr]: https://github.com/klaussilveira/phpcs-psr
[phpcsfixer]: http://cs.sensiolabs.org/
