---
isChild: true
title: Camadas de Abstração
anchor: camadas_de_abstracao_de_banco_de_dados
---

## Camadas de Abstração {#camadas_de_abstracao_de_banco_de_dados_title}

Muitos frameworks fornecem sua própria camada de abstração que pode ou não sobrepor o [PDO][1]. Estes muitas vezes 
simulam características de um sistema de banco de dados que outro banco de dados não possui envolvendo suas consultas 
em métodos PHP, dando-lhe a abstração real do banco de dados em vez de apenas a abstração da conexão como o PDO oferece.

Isto obviamente adiciona um pequeno peso, mas se você estiver construindo uma aplicação portátil que precise trabalhar 
com MySQL, PostgreSQL e SQLite, então este pequeno peso vai valer a pena pela limpeza e menos linhas de código.

Algumas camadas de abstração foram construídas utilizando o padrão de namespaces da [PSR-0][psr0] ou [PSR-4][psr4] para 
que possa ser instalado em qualquer aplicação que você queira.

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [Propel][7]
* [ZF2 Db][4]

[1]: http://www.php.net/manual/en/book.pdo.php
[2]: http://www.doctrine-project.org/projects/dbal.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[6]: https://github.com/auraphp/Aura.Sql
[7]: http://propelorm.org/

[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md