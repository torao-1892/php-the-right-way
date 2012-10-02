---
isChild: true
---

## Desenvolvimento Orientado a Testes

Da [Wikipedia](http://en.wikipedia.org/wiki/Test-driven_development):

> O desenvolvimento orientado a testes (TDD) é um processo de desenvolvimento que se baseia na repetição de um ciclo de desenvolvimento bem curto: primeiro o desenvolvedor escreve um caso de teste automatizado que falha, definindo uma melhoria ou uma nova função desejada, em seguida produz o código para passar no teste, e finalmente refatora o novo código pelos padrões aceitáveis. Kent Back, que é creditado como quem desenvolveu ou "redescobriu" essa técnica, afirmou em 2003 que o TDD encoraja design simples e inspira confiança.

Existem vários tipos diferentes de testes que você pode fazer para sua aplicação.

### Testes Unitários

Testes unitários são uma metodologia de programação que garante que as funções, as classes e os métodos estão funcionando como
esperado, desde o momento que você os constrói até o fim do ciclo de desenvolvimento. Verificando como os
valores entram e saem em várias funções e métodos, você pode garantir que a lógica interna está
funcionando corretamente. Utilizando Injeção de Dependências e construindo classes "mock" e stubs, você pode verificar se
as dependências foram utilizadas corretamente para uma cobertura de testes ainda melhor.

Quando você criar uma classe ou função, você deveria criar um teste unitário para cada comportamento que ela deveria ter. Num nível bem básico, você deveria
garantir que são emitidos erros quando você envia argumentos errados e garantir que tudo funciona bem se você enviar argumentos válidos.
Isso ajudará a garantir que, quando você alterar sua classe ou sua função posteriormente no ciclo de
desenvolvimento, as funcionalidades antigas continuarão funcionando como esperado. A única alternativa a isso seria
usar var_dump() em um test.php, o que não é o certo a fazer na construção de uma aplicação - grande ou pequena.

O outro uso para testes unitários é contribuir para projetos open source. Se você puder escrever um teste que demonstra uma funcionalidade
incorreta (i.e. uma falha), em seguida consertá-la e mostrar o teste passando, os patches serão muito mais suscetíveis a serem aceitos. Se
você estiver em um projeto que aceite pull requests, você deveria sugerir isso como um requisito.

O [PHPUnit](http://phpunit.de) é o framework de testes de fato para escrever testes unitários em aplicações
PHP, mas existem várias alternativas:

* [SimpleTest](http://simpletest.org)
* [Enhance PHP](http://www.enhance-php.com/)
* [PUnit](http://punit.smf.me.uk/)

### Integration Testing

From [Wikipedia](http://en.wikipedia.org/wiki/Integration_testing):

> Integration testing (sometimes called Integration and Testing, abbreviated "I&T") is the phase in software testing in which individual software modules are combined and tested as a group. It occurs after unit testing and before validation testing. Integration testing takes as its input modules that have been unit tested, groups them in larger aggregates, applies tests defined in an integration test plan to those aggregates, and delivers as its output the integrated system ready for system testing.

Many of the same tools that can be used for unit testing can be used for integration testing as many
of the same principles are used.

### Functional Testing

Sometimes also known as acceptance testing, functional testing consists of using tools to create automated
tests that actually use your application instead of just verifying that individual units of code are behaving
correctly and that individual units can speak to each other correctly. These tools typically work using real
data and simulating actual users of the application.

#### Functional Testing Tools

* [Selenium](http://seleniumhq.com)
* [Mink](http://mink.behat.org)
* [Codeception](http://codeception.com) is a full-stack testing framework that includes acceptance testing tools
