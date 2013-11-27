---
isChild: true
---

## Serialize {#serialize_title}

Como armazenar ou transmitir valores PHP sem perder sua naturalidade e sua estrutura? 
Por exemplo, você possui um objeto já com seus atributos definidos e deseja armazenar esse estado que ele se encontra agora para poder usar uma outra hora.
Você pode utilizar a serialização para colocar todas as informações dentro de um texto, e quando você quiser utilizar novamente é só resgatar os valores.
Mas como fazer isso?

### Serializar Dados
Tendo uma estrutura de dados com valores você já pode guardar o seu atual estado. Como por exemplo em um array.

{% highlight php %}
<?php
$array = array(1, 2, 3, 4, 5);
echo serialize($array);
// Resultado: a:5:{i:0;i:1;i:1;i:2;i:2;i:3;i:3;i:4;i:4;i:5;}
?>
{% endhighlight %}

### Restaurar Dados Serializados
Para obter os valores de volta, basta utilizar a função unserialize e em seu parametro colocar o texto já serializado.
Você terá como retorno a estrutura e os dados que foram serializados!

{% highlight php %}
<?php
$arraySerialized = 'a:5:{i:0;i:1;i:1;i:2;i:2;i:3;i:3;i:4;i:4;i:5;}';
var_dump(unserialize($arraySerialized));
/* Resultado:
array
 0 => int 1
 1 => int 2
 2 => int 3
 3 => int 4
 4 => int 5 */

{% endhighlight %}

Isso pode ser utilizado para qualquer conjunto de dados, como objeto, array, entre outros.
Caso o valor do parâmetro do unserialize não for texto ele dispara um E_NOTICE, para que isso não ocorra coloque o operador @ na função unserialize (@unserialize($arraySerialized))

* [Leia sobre Serialize][serialize]

[serialize]: http://php.net/manual/pt_BR/function.serialize.php
