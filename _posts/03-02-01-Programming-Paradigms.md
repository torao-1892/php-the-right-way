---
isChild: true
---

## Paradigmas de programação

O PHP é uma linguagem dinâmica e flexível, que suporta uma variedade de técnicas de programação. Ele evoluiu drasticamente com o passar dos anos, notavelmente adicionando um sólido modelo de orientação a objetos no PHP 5.0 (2004), funções anônimas e namespaces no PHP 5.3 (2009) e traits no PHP 5.4 (2012).

### Programação orientada a objetos

* [Leia sobre PHP orientado a objetos][oop]
* [Leia sobre Traits][traits]

### Programação funcional

PHP possui funções anônimas desde o PHP 5.3:

{% highlight php %}
<?php
$saudacao = function($nome)
{
    print("Oi {$nome}");
};

$saudacao('Mundo');
{% endhighlight %}

* [Leia sobre Funções anônimas][anonymous-functions]
* [Leia sobre invocar funções dinamicamente com `call_user_func_array`][call-user-func-array]

### Meta Programação

Desenvolvedores Ruby costumam dizer que o PHP carece de `method_missing`, mas ela está disponível como `__call()`. Existem muitos outros Métodos Mágicos disponíveis, como  `__get()`, `__set()`, `__clone()`, `__toString()`, etc.

* [Leia sobre Métodos Mágicos][magic-methods]
* [Leia sobre Reflexão][reflection]

[namespaces]: http://php.net/manual/en/language.namespaces.php
[overloading]: http://uk.php.net/manual/en/language.oop5.overloading.php
[oop]: http://www.php.net/manual/en/language.oop5.php
[anonymous-functions]: http://www.php.net/manual/en/functions.anonymous.php
[magic-methods]: http://php.net/manual/en/language.oop5.magic.php
[reflection]: http://www.php.net/manual/en/intro.reflection.php
[traits]: http://www.php.net/traits
[call-user-func-array]: http://php.net/manual/en/function.call-user-func-array.php
