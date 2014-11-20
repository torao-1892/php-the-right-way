---
title: Problema Complexo
isChild: true
anchor: problema_complexo
---

## Problema Complexo {#problema_complexo_title}

Se você já leu sobre Inversão de Dependência, então você provavelmente viu os termos *"Inversão de Controle"* ou
*"Princípio da Inversão de Dependência"*.
Estes são os problemas complexos que a Inversão de Dependência resolve.

### Inversão de Controle

Inversão de controle é como se diz, "invertendo o controle" de um sistema para manter os controles organizacionais
totalmente separados dos seus objetos.
Em termos de Dependency Injection, isto significa desacoplar as dependências para controlá-las e instanciá-las em outro 
lugar do sistema.

Por anos, os frameworks PHP usam a Inversão de Controle, no entanto, a questão é: que parte do controle está invertendo, 
e onde? Por exemplo, frameworks MVC, em geral, fornecem um super objeto ou um controlador base que outros controladores 
devem extender para obter acesso as suas dependências. Isto **é** Inversão de Controle, no entanto, em vez de desacoplar 
as dependências, este método simplesmente as mudou.

Dependency Injection permite resolver de forma mais elegante este problema apenas injetando a dependência que precisamos, 
quando precisamos dela, sem a necessidade de quaisquer dependências no código.

### Princípio da Inversão de Dependência

O Princípio da Inversão de Dependência é o "D", no S.O.L.I.D, define o princípio de design da orientação a objeto que 
afirma que *"Depende de uma Abstração. Não depende de Objetos concretos"*. Simplificando, isto significa que nossas 
dependências devem ser classes de interfaces/contratos ou class abstratas em vez de implementações concretas.
Podemos facilmente refatorar o exemplo abaixo para seguir este princípio.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(AdapterInterface $adapter)
    {
        $this->adapter = $adapter;
    }
}

interface AdapterInterface {}

class MysqlAdapter implements AdapterInterface {}
{% endhighlight %}

Existem vários benefícios para a classe `Database`, agora, dependendo de uma interface em vez de um objeto concreto.

Considerando que você trabalha em uma equipe e o adaptador está sendo trabalhado por um colega. No primeiro exemplo,
teriamos que esperar o colega dizer que terminou o adaptador antes que pudéssemos simulá-la(mock) nos testes unitários.
Agora, que a denpendência é uma interface/contrato podemos facilmente simulá-la(mock) sabendo que o colega vai
construir o adaptador com base neste contrato.

Um benefício ainda maior para este método é que nosso código, agora, está mais escalável. Se um ano depois decidir
migrar para um banco de dados diferente, podemos escrever um novo adaptador que implementa a interface original e
injetá-lo, não seria preciso nenhuma refatoração, pois o adaptador segue o contrato definido pela interface.