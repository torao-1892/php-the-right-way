---
isChild: true
---

## Filtro de Dados

Nunca, jamais (nunca mesmo), confie em entradas externas feitas no seu código PHP. Sempre higienize(sanitize) e valide
as entradas externas antes de utilizá-las no seu código. As funcões `filter_var` e `filter_input` podem higienizar textos e validar formatos (e.g.
endereços de email).

Entradas externas podem ser qualquer coisa: dados de entrada de formulário `$_GET` ou `$_POST`, alguns valores na superglobal
`$_SERVER` e o corpo da requisição HTTP via `fopen('php://input', 'r')`. Lembre-se, entradas externas não estão
limitadas a dados de formulários enviados pelo usuário. Arquivos carregados e baixados, valores em sessões, dados dos cookies
e dados de web services de terceiros também são entradas externas.

Enquanto o dado externo puder ser armazenado, combinado ou acessado posteriormente, ele continua sendo uma entrada externa. Todo
momento que você processar, emitir, concatenar ou incluir dados no seu código, pergunte a si mesmo se
eles foram filtrados adequadamente e se são confiáveis.

Os dados podem ser _filtrados_ de maneiras diferentes baseando-se em sua finalidade. Por exemplo, quando entradas externas não filtradas são passadas
para uma saída de página HTML, elas podem executar HTML e JavaScript no seu site! Isso é conhecido como Cross-Site
Scripting (XSS) e pode ser um ataque bem perigoso. Um modo de evitar o XSS é higienizar todas as tags HTML
da entrada, removendo as tags ou escapando-as usando entidades HTML.

Outro exemplo é ao passar opções para execução na linha de comando. Isso pode ser extremamente perigoso
(e geralmente é má ideia), mas você pode usar a função embutida `escapeshellarg` para higienizar os argumentos
executados.

One last example is accepting foreign input to determine a file to load from the filesystem. This can be exploited by
changing the filename to a file path. You need to remove "/", "../", [null bytes][6], or other characters from the file path so it can't
load hidden, non-public, or sensitive files.

* [Learn about data filtering][1]
* [Learn about `filter_var`][4]
* [Learn about `filter_input`][5]
* [Learn about handling null bytes][6]

### Sanitization

Sanitization removes (or escapes) illegal or unsafe characters from foreign input.

For example, you should sanitize foreign input before including the input in HTML or inserting it
into a raw SQL query. When you use bound parameters with [PDO](#databases), it will
sanitize the input for you.

Sometimes it is required to allow some safe HTML tags in the input when including it in the HTML
page. This is very hard to do and many avoid it by using other more restricted formatting like
Markdown or BBCode, although whitelisting libraries like [HTML Purifier][html-purifier] exists for
this reason.

[See Sanitization Filters][2]

### Validation

Validation ensures that foreign input is what you expect. For example, you may want to validate an
email address, a phone number, or age when processing a registration submission.

[See Validation Filters][3]

[1]: http://www.php.net/manual/en/book.filter.php
[2]: http://www.php.net/manual/en/filter.filters.sanitize.php
[3]: http://www.php.net/manual/en/filter.filters.validate.php
[4]: http://php.net/manual/en/function.filter-var.php
[5]: http://www.php.net/manual/en/function.filter-input.php
[6]: http://php.net/manual/en/security.filesystem.nullbytes.php
[html-purifier]: http://htmlpurifier.org/
