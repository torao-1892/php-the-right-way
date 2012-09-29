---
isChild: true
---

## Exceções

As exceções são uma parte padrão da maioria das linguagens de progração populares, mas elas são frequentemente negligenciadas pelos programadores PHP.
Linguagens como o Ruby são extremamente fortes nas Exceções, por isso sempre que algo dá errado, como numa falha de requisição HTTP,
ou uma consulta incorreta num banco de dados, ou mesmo se um arquivo de imagem não puder ser encontrada, o Ruby (ou as gems que estiverem sendo usadas) irá lançar
uma exceção na tela fazendo com que você saiba instantaneamente que há um erro.

O próprio PHP é bem fraco nessa parte, e uma chamada para `file_get_contents()` no geral irá apenas te retornar um `FALSE` e um erro warning.
Muitos frameworks PHP antigos como o CodeIgniter irão apenas retornar um false, registrar uma mensagem nos seus logs proprietários e talvez
permitir que você use um método como `$this->upload->get_error()` para ver o que deu errado. O problema aqui é que você precisa
procurar por um erro e verificar a documentação para ver qual é o método de erro para aquela classe, em vez de ter isso extremamente
óbvio.

Outro problema é quando as classes lançam um erro na tela automaticamente e terminam o processamento. Quando você faz isso, você
não permite que outro desenvolvedor possa tratar aquele erro dinamicamente. As exceções devem ser lançadas para alertar o desenvolvedor
sobre um erro, e então deixá-lo escolher como tratá-lo. Por exemplo:

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // A validação falhou
}
catch(Fuel\Email\SendingFailedException $e)
{
    // O driver não pode enviar o email
}
{% endhighlight %}

### Exceções SPL

Uma Exceção por padrão não tem significado e a forma mais comum de dar um sentido para ela é definindo seu nome:

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

Isso significa que você pode adicionar múltiplos blocos catch e tratar exceções distintas de formas diferentes. Isso pode te levar
a criar <em>várias</em> Exceções personalizadas, algumas das quais podem ser evitadas usando as Exceções SPL
fornecidas na [extensão SPL][splext].

Se, por exemplo, você usar o Método Mágico `__call()` e um método inválido for requisitado, em vez de lançar uma Exceção
padrão que é vaga, ou criar uma Exceção personalizada apenas para isso, você poderia apenas `throw new BadFunctionCallException;`.

* [Leia sobre as Exceções][exceptions]
* [Leia sobre as Exceções SPL][splexe]
* [Exceções Aninhadas no PHP][nesting-exceptions-in-php]
* [Melhores Práticas para Exceção em PHP 5.3][exception-best-practices53]

[exceptions]: http://php.net/manual/en/language.exceptions.php
[splexe]: http://php.net/manual/en/spl.exceptions.php
[splext]: /#standard_php_library
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
