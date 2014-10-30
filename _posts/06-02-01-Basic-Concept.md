---
title: Conceito Básico
isChild: true
anchor: conceito_basico
---

## Conceito Básico {#conceito_basico_title}

Demostraremos o conceito com um simples exemplo.

Temos uma classe `Database` que requer um adaptador para se comunicar com o banco de dados. Instanciaremos o adaptador
no construtor e assim criamos uma forte de dependência. Isto dificulta os testes e significa que a classe `Database`
está fortemente acoplada ao adaptador.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct()
    {
        $this->adapter = new MySqlAdapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

Este código pode ser refatorado para usar a Dependency Injection para desacoplar a dependência.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(MySqlAdapter $adapter)
    {
        $this->adapter = $adapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

Agora, damos a classe `Database` a sua dependência em vez de criar dentro dela. Poderiamos também, criar um método
que aceitaria um argumento da dependência e defini-la dessa forma, ou definir a propriedade `$adapter` como `public`
para defini-la diretamente.
