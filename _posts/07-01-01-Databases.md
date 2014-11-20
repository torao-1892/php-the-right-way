---
title: Banco de Dados
anchor: banco_de_dados
---

# Bancos de Dados {#banco_de_dados_title}

Muitas vezes o seu código PHP usará um banco de dados para persistir informações. Você tem algumas opções para
conectar e interagir como seu banco de dados. A opção recomendada _até o PHP 5.1.0_ era usar os drivers nativos, como
o [mysqli], o [pgsql], [mssql]  etc.

Drivers nativos são excelentes se você estiver usando apenas _um_ banco de dados em sua aplicação, mas se, por exemplo,
você estiver usando o MySQL e um pouco de MSSQL, ou você precisar conectar em um banco de dados Oracle, aí você não
poderá usar os mesmos drivers. Você precisará aprender um API totalmente nova para cada um dos bancos de dados &mdash;
e isso pode ficar chato.

## MySQL Extension 

A extensão [mysql] para o PHP não está mais em desenvolvimento ativo e foi [oficialmente deprecada no PHP 5.5.0]. Isso 
significa que ela será removida dentro de alguns lançamentos das próximas versões. Se você estiver usando funções que 
inicial com `mysql_*` como a `mysql_connect()` e a `mysql_query()` em suas aplicações você irá se deparar com uma 
reescrita em algum momento no futuro, por isso a melhor opção é substituir o uso do mysql pelo mysqli ou pela PDO na sua 
aplicação dentro de sua própria agenda de desenvolvimento, assim você não terá que correr lá na frente. 

**Se você estiver começando do zero então não utilize de forma nenhuma a
extensão mysql: use a [extensão MySQLi][mysqli], ou use a [PDO].**

* [PHP: Choosing an API for MySQL](http://php.net/manual/en/mysqlinfo.api.choosing.php)
* [PDO Tutorial for MySQL Developers](http://wiki.hashphp.org/PDO_Tutorial_for_MySQL_Developers)

## Extensão PDO

A [PDO] é uma biblioteca para abstração de conexões a bancos de dados &mdash; embutida no PHP desde a versão 5.1.0 
&mdash; que fornece uma interface comum para conversar com vários bancos de dados diferentes. Por exemplo, vocẽ pode 
usar basicamente o mesmo código para fazer a interface com o MySQL ou SQLite:

{% highlight php %}
// PDO + MySQL
$pdo = new PDO('mysql:host=example.com;dbname=database', 'user', 'password');
$statement = $pdo->query("SELECT some\_field FROM some\_table");
$row = $statement->fetch(PDO::FETCH_ASSOC);
echo htmlentities($row['some_field']);

// PDO + SQLite
$pdo = new PDO('sqlite:/path/db/foo.sqlite');
$statement = $pdo->query("SELECT some\_field FROM some\_table");
$row = $statement->fetch(PDO::FETCH_ASSOC);
echo htmlentities($row['some_field']);
{% endhighlight %}

A PDO não irá traduzir
suas consultas SQL ou emular funcionalidades que não existem; ela é feita puramente para conectar múltiplos tipos de
bancos de dados com a mesma API.

Mais importante, a `PDO` permite que você injete de forma segura entradas externas (e.g IDs) em suas consultas SQL
sem se preocupar com ataques de SQL injection.
Isso é possível usando instruções PDO (PDO statements) e parâmetros restritos (bound parameters).

Vamos assumir que um script PHP recebe um ID numérico como parâmetro de uma consulta. Este ID deve ser usado para
buscar um registro de um usuário no banco de dados. Essa é a forma `errada` de fazer isso:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:/path/db/users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NÃO!
{% endhighlight %}

Esse código é péssimo. Você está inserindo um parâmetro bruto na sua consulta SQL. Isso fará você ser hackeado num
piscar de olhos, usando uma prática chamada [SQL Injection](http://wiki.hashphp.org/Validation). Apenas imagine se um 
hacker passar como parâmetro um `id` inventivo chamando uma URL como `http://domain.com/?id=1%3BDELETE+FROM+users`. 
Isso irá definir a variável `$_GET['id']` como `id=1;DELETE FROM users`, o que irá excluir todos os seus usuários. Em 
vez disso, você deveria higienizar (sanitize) a entrada do ID usando parâmetros restritos da PDO.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:/path/db/users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$stmt->bindParam(':id', $_GET['id'], PDO::PARAM_INT); //<-- Higienizado automaticamente pela PDO
$stmt->execute();
{% endhighlight %}

Esse é o código correto. Ele usa um parâmetro restrito em uma instrução PDO. Assim a entrada externa do ID é escapada
antes de ser introduzida no banco de dados, prevenindo contra potenciais ataques de SQL injection.

* [Leia mais sobre a PDO]

Você também deve estar ciente de que usam recursos do servidor e não é raro ter esses recursos esgotados se essas
conexões não forem implicitamente fechadas, entretanto isso é mais comum em outras linguagens. Com PDO você pode
implicitamente fechar as conexões pela destruição dos objetos garantindo que todas as referências a ele forem excluídas,
ex. atribuindo NULL a elas. Se você não fizer isso explicitamente o PHP irá fechar todas as conexões quando seu script
terminar - a não ser é claro que você esteja usando conexões persistentes.

* [Leia mais sobre conexões PDO]

[Leia mais sobre a PDO]: http://www.php.net/manual/en/book.pdo.php
[Leia mais sobre conexões PDO]: http://php.net/manual/en/pdo.connections.php
[oficialmente deprecada no PHP 5.5.0]: http://php.net/manual/en/migration55.deprecated.php
[SQL Injection]: http://wiki.hashphp.org/Validation

[pdo]: http://php.net/pdo
[mysql]: http://php.net/mysql
[mysqli]: http://php.net/mysqli
[pgsql]: http://php.net/pgsql
[mssql]: http://php.net/mssql