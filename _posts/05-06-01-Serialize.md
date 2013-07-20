---
isChild: true
---

## Serilize {#serialize_title}

### Serializar Dados

O processo de salvar um objeto em um meio de armazenamento ou transimessão de dados, seja de forma binária ou em forma de texto. Esses Bytes ou texto pode ser usada para recriar um objeto com o mesmo estado com o qual foi salvo. 
Por exemplo, você joga um jogo e quer pausar ele, porém não queis perder os seus itens/objeto, você salva o jogo, para quando quiser retornar a jogar você pode continuar do local que parou.
Com isso você fez a serialização dos objetos do seu jogo. 
Em PHP funciona do mesmo jeito.


{% highlight php %}
<?php
$array = array(1, 2, 3, 4, 5);
echo serialize($array);
// Resultado: a:5:{i:0;i:1;i:1;i:2;i:2;i:3;i:3;i:4;i:4;i:5;}
?>
{% endhighlight %}

### Restaurar Dados Serializados


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