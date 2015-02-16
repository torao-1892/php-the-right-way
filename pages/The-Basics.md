---
layout: page
title: The Basics
---

# O Básico

## Operadores de Comparação

Operadores de Comparação são frequentemente negligenciados em PHP, o que pode levar a muitos resultados inesperados. Um
desses problemas decorre de comparações estritas (comparações entre booleanos e inteiros).

{% highlight php %}
<?php
$a = 5;   // 5 como inteiro

var_dump($a == 5);       // comparação de valores; retorna true
var_dump($a == '5');     // comparação de valores (ignorando os tipos); retorna true
var_dump($a === 5);      // comparação de tipos e valores (integer vs. integer); retorna true
var_dump($a === '5');    // comparação de tipos e valores (integer vs. string); retorna false

/**
 * Comparações Estritas
 */
if (strpos('testing', 'test')) {    // 'test' é encontrado na posição 0, que é interpretado como o booleano 'false'
    // código...
}

vs.

if (strpos('testing', 'test') !== false) {    // true, já que uma comparação estrita foi feita (0 !== false)
    // código...
}
{% endhighlight %}

* [Operadores de Comparação](http://php.net/manual/en/language.operators.comparison.php)
* [Tabela de Comparação](http://php.net/manual/en/types.comparisons.php)

## Estrutura de Controle

### Estruturas Condicionais

Quando as declarações 'if/else' são usadas em uma função ou classe, é um equívoco comum pensar que 'else' precisa ser
usado em conjunto para declarar resultados em potencial. Entretanto se o resultado serve para definir o valor a ser
retornado 'else' não é necessário já que 'return' irá terminar a função, fazendo com que o uso de 'else' se torne
discutível.

{% highlight php %}
<?php
function test($a)
{
    if ($a) {
        return true;
    } else {
        return false;
    }
}

// vs

function test($a)
{
    if ($a) {
        return true;
    }
    return false;    // else não é necessário
}
{% endhighlight %}

* [Estrutura Condicionais](http://php.net/manual/en/control-structures.if.php)

### Estruturas de Decisão

Estruturas de decisão são uma excelente forma de evitar escrever intermináveis estruturas condicionais, mas existem
alguns pontos sobre os quais deve-se ficar atento:

- Estruturas de decisão só comparam valores, e não tipos (equivalente a '==')
- Elas passam por caso a caso até que uma correspondencia seja encontrada, então default é usado (caso esteja definido)
- Sem que haja um 'break', elas continuarão a executar cada caso até que encontrem um break/return
- Dentro de uma função o uso de 'return' remove a necessidade do uso de 'break' já que isso encerra essa função

{% highlight php %}
<?php
$answer = test(2);    // tanto o código para o 'case 2' quanto para o 'case 3' será executado

function test($a)
{
    switch ($a) {
        case 1:
            // código...
            break;             // break é usado para terminar a estrutura de decisão
        case 2:
            // código...       // sem o break, a comparação ira continuar em 'case 3'
        case 3:
            // código...
            return $result;    // dentro de uma função, 'return' termina essa função
        default:
            // código...
            return $error;
    }
}
{% endhighlight %}

* [Estruturas de Decisão](http://php.net/manual/en/control-structures.switch.php)
* [PHP Switch](http://phpswitch.com/)

## Namespace Global

Quando estiver usando namespaces você pode reparar que funções internas ficam escondidas por funções que você mesmo
escreveu. Para corrigir isso refira a funções globais através do uso de uma contra-barra antes do nome da função.

{% highlight php %}
<?php
namespace phptherightway;

function fopen()
{
    $file = \fopen();    // O nome da nossa função é igual a de uma função interna.
                         // Execute a função global através da inclusão de '\'.
}

function array()
{
    $iterator = new \ArrayIterator();    // ArrayIterator é uma classe interna. Usar seu nome sem uma contra-barra
                                         // tentará localizar essa função dentro do namespace
}
{% endhighlight %}

* [Espaço Global](http://php.net/manual/en/language.namespaces.global.php)
* [Regras Globais](http://php.net/manual/en/userlandnaming.rules.php)

## Strings

### Concatenação

- Se sua linha passar do tamanho recomendado (120 caracteres), considere concatenar sua linha
- Para facilitar a leitura é melhor usar operadores de concatenação do que operadores de concatenação e atribuição
- Enquanto dentro do escopo original da variável, indente quando a concatenação usar uma nova linha


{% highlight php %}
<?php
$a  = 'Multi-line example';    // operador de concatenação e atribuição (.=)
$a .= "\n";
$a .= 'of what not to do';

vs.

$a = 'Multi-line example'      // operador de concatenação (.)
    . "\n"                     // indentando novas linhas
    . 'of what to do';
{% endhighlight %}

* [Operadores de Strings](http://php.net/manual/en/language.operators.string.php)

### Tipos de Strings

Tipos de string são uma característica constante na comunidade PHP, mas talvez essa seção possa explicar as diferenças
entre os tipos de strings e seus usos e benefícios.

#### Aspas Simples

As aspas simples são utilizadas para indicar uma "string literal". Strings literais não tenta analisar caracteres 
especiais ou variáveis.

Se estiver usando aspas simples, você pode digitar um nome de variável em uma string assim: `'some $thing'` e você verá 
a saída exata `some $thing`. Se você estiver usando aspas duplas, irá tentar avaliar a variável `$thing` e então 
mostrará erros se nenhuma variável for encontrada.

{% highlight php %}
<?php
echo 'This is my string, look at how pretty it is.';    // sem necessidade de interpretar uma string simples

/**
 * Saída:
 *
 * This is my string, look at how pretty it is.
 */
{% endhighlight %}

* [Aspas Simples](http://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.single)

#### Aspas Duplas

Aspas Duplas são o canivete suíço das strings, mas são mais lentas devido a interpretação das strings. Ele não só irá 
analisar as variáveis como mencionado acima mas também todos os tipos de caracteres especiais, como `\n` para nova 
linha, `\t` para identação, etc.

{% highlight php %}
<?php
echo 'phptherightway é ' . $adjective . '.'      // Um exemplo com aspas simples que usa concatenação múltipla para
    . "\n"                                       // variáveis e escapar strings
    . 'I love learning' . $code . '!';

// vs

echo "phptherightway is $adjective.\n I love learning $code!"  // Em vez de concatenação múltipla, aspas duplas
                                                               // nos permitem utilizar strings interpretáveis
{% endhighlight %}

Aspas duplas que contém variáveis; Isto é chamado "interpolação".

{% highlight php %}
<?php
$juice = 'plum';
echo "I like $juice juice";    // Output: I like plum juice
{% endhighlight %}

Quando usando interpolação, são comuns os casos onde a variável pode estar colada com outro
caracter. Isso fará com que o PHP não consiga interpretar essa variável pelo fato dela estar sendo camuflada. 

Para corrigir esse problema envolva a variável em um par de chaves.

{% highlight php %}
<?php
$juice = 'plum';
echo "I drank some juice made of $juices";    // $juice cannot be parsed

// vs

$juice = 'plum';
echo "I drank some juice made of {$juice}s";    // $juice will be parsed

/**
 * Variáveis complexas também serão interpretadas com o uso de chaves
 */

$juice = array('apple', 'orange', 'plum');
echo "I drank some juice made of {$juice[1]}s";   // $juice[1] will be parsed
{% endhighlight %}

* [Aspas Duplas](http://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.double)

#### Sintaxe Nowdoc

A Sintaxe Nowdoc foi introduzida no PHP 5.3 e internamente se comporta da mesma forma que as aspas simples exceto que é
adequada para o uso de strings de múltiplas linhas sem a necessidade de concatenação.

{% highlight php %}
<?php
$str = <<<'EOD'            // iniciada por <<<
Example of string
spanning multiple lines
using nowdoc syntax.
$a does not parse.
EOD;                       // fechando 'EOD' precisa estar na sua própria linha, e no ponto mais a esquerda

/**
 * Output:
 *
 * Example of string
 * spanning multiple lines
 * using nowdoc syntax.
 * $a does not parse.
 */
{% endhighlight %}

* [Sintaxe Nowdoc](http://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.nowdoc)

#### Sintaxe Heredoc

A Sintaxe Heredoc se comporta internamente da mesma forma que as aspas duplas exceto que é adequada para o uso de strings
de múltiplas linhas sem a necessidade de concatenação.

{% highlight php %}
<?php
$a = 'Variables';

$str = <<<EOD             // iniciada por <<<
Example of string
spanning multiple lines
using heredoc syntax.
$a are parsed.
EOD;                      // fechando 'EOD' precisa estar na sua própria linha, e no ponto mais a esquerda

/**
 * Output:
 *
 * Example of string
 * spanning multiple lines
 * using heredoc syntax.
 * Variables are parsed.
 */
{% endhighlight %}

* [Sintaxe Heredoc](http://www.php.net/manual/en/language.types.string.php#language.types.string.syntax.heredoc)

### O que é mais rápido?

Há um mito por aí que usar aspas simples em strings são interpretadas mais rápida do que usar aspas duplas. Isso não é fundamentalmente falso.

Se você estiver definindo uma string única e não concatenar valores ou qualquer coisa complicada, então aspas simples ou duplas serão idênticas. Não será mais rápido.

Se você está concatenando várias strings de qualquer tipo, ou interpolar valores em uma string entre aspas duplas, então os resultados podem variar. Se você estiver trabalhando com um pequeno número de valores, a concatenação é minuciosamente mais rápida. Com um monte de valores, interpolação é minuciosamente mais rápida.

Independentemente do que você está fazendo com strings, nenhum dos tipos vai ter qualquer impacto perceptível sobre a sua aplicação.
Tentar reescrever código para usar um ou o outro é sempre um exercício de futilidade, de modo a evitar este micro-otimização, a menos que você realmente compreenda o significado e o impacto das diferenças.

[Desmentindo o mito de desempenho das aspas simples]: http://nikic.github.io/2012/01/09/Disproving-the-Single-Quotes-Performance-Myth.html


## Operadores Ternários

O uso de operadores ternários é uma ótima forma de condensar seu código, mas eles são geralmente usados em excesso.
Apesar de operações ternárias poderem ser agrupadas e aconselhado usar uma por linha para aumentar a legibilidade.

{% highlight php %}
<?php
$a = 5;
echo ($a == 5) ? 'yay' : 'nay';
{% endhighlight %}

// vs

{% highlight php %}
$b = 10;
echo ($a) ? ($a == 5) ? 'yay' : 'nay' : ($b == 10) ? 'excessive' : ':(';    // excesso de agrupamento sacrifica a legibilidade
{% endhighlight %}

Para usar 'return' em um operador ternário utilize a sintaxe correta.

{% highlight php %}
<?php
$a = 5;
echo ($a == 5) ? return true : return false;    // esse exemplo irá disparar um erro

// vs

$a = 5;
return ($a == 5) ? 'yay' : 'nope';    // esse exemplo irá retornar 'yay'
{% endhighlight %}

Note que você não precisa usar um operador ternário para retornar um valor booleano. Um exemplo disto seria.

{% highlight php %}
<?php
$a = 3;
return ($a == 3) ? true : false; // esse exemplo irá retornar true ou false se $a == 3

// vs

$a = 3;
return $a == 3; // esse exemplo irá retornar true ou false se $a == 3

{% endhighlight %}

Isso também pode ser dito para as operações (===, !==, !=, == etc).

#### Utilizando parênteses com operadores ternários para formato e função

Quando se utiliza um operador ternário, os parênteses podem melhorar a legibilidade do código e também incluir as uniões 
dentro de blocos de instruções. Um exemplo de quando não há nenhuma exigência para usar de parênteses é:

{% highlight php %}
<?php
$a = 3;
return ($a == 3) ? "yay" : "nope"; // vai retornar yay ou nope se $a == 3

// vs

<?php
$a = 3;
return $a == 3 ? "yay" : "nope"; // vai retornar yay ou nope se $a == 3
{% endhighlight %}

O uso de parênteses também nos dá a capacidade de criar união dentro de um bloco de declaração onde o bloco será 
verificado como um todo. Tal como este exemplo abaixo que retornará verdadeiro se ambos ($a == 3 e $b == 4) são 
verdadeiras e $c == 5 também é verdadeiro.

{% highlight php %}
<?php
return ($a == 3 && $b == 4) && $c == 5;
{% endhighlight %}

Outro exemplo é o trecho de código abaixo que vai returnar true se ($a != 3 e $b != 4) ou $c == 5.

{% highlight php %}
<?php
return ($a != 3 && $b != 4) || $c == 5;
{% endhighlight %}

* [Operadores Ternários](http://php.net/manual/en/language.operators.comparison.php)

## Declaração de Variáveis

As vezes  programadores tentam tornar seu código mais limpo declarando variáveis predefinidas com um nome diferente. O
que isso faz na realidade e dobrar o consumo de memória do script. No exemplo abaixo, digamos que uma string de exemplo
contém 1MB de dado válido, copiando a variável você aumenta o consumo de memória durante a execução para 2MB.

{% highlight php %}
<?php
$about = 'Uma string com texto bem longo';    // usa 2MB de memória
echo $about;

// vs

echo 'Uma string com texto bem longo';        // usa 1MB de memória
{% endhighlight %}

* [Dicas de Performance](http://web.archive.org/web/20140625191431/https://developers.google.com/speed/articles/optimizing-php)