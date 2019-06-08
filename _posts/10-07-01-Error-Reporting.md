---
title: Relatório de Erros
isChild: true
anchor: relatorio_de_erros
---

## Relatório de Erros {#relatorio_de_erros_title}

O registro de erros pode ser útil para encontrar pontos problemáticos em sua aplicação, mas isso também pode expor
informações sobre a estrutura de sua aplicação para o mundo exterior. Para proteger efetivamente sua aplicação dos
problemas que poderiam ser causados com a exposição dessas mensagens, você precisa configurar seu servidor de formas
diferentes quando em desenvolvimento versus quando em produção (no ar).

### Desenvolvimento

Para mostrar erros no seus ambiente de <strong>desenvolvimento</strong>, configure as definições a seguir no seu `php
ini`:

{% highlight ini %}
display_errors = On
display_startup_errors = On
error_reporting = -1
log_errors = On
{% endhighlight %}

Do [php.net](http://php.net/function.error-reporting):

> Passar o valor -1 irá mostrar todos os erros possíveis, até mesmo quando novos níveis e constantes forem adicionados 
em versões futuras do PHP. A constante E_ALL também se comporta desta maneira a partir do PHP 5.4.

O nível de error `E_STRICT` foi introduzido no 5.3.0 e não faz parte do `E_ALL`, contudo ele tornou-se parte do `E_ALL
` no 5.4.0. O que isso significa?  Que para mostrar todos os erros possíveis na versão 5.3 você precisa usar `-1` ou 
`E_ALL | E_STRICT`. 

**Reportando todos os erros possíveis em diferentes versões do PHP**

* &lt; 5.3 `-1` ou `E_ALL`
* &nbsp; 5.3 `-1` ou `E_ALL | E_STRICT`
* &gt; 5.3 `-1` ou `E_ALL`

### Produção

Para esconder os erros no seu ambiente de <strong>produção</strong>, configure seu `php.ini` assim:

{% highlight ini %}
display_errors = Off
display_startup_errors = Off
error_reporting = E_ALL
log_errors = On
{% endhighlight %}

Com essas configurações em produção, os erros continuarão sendo registrados nos logs de erros do servidor web, mas
eles não serão mostrados para o usuário. Para mais informações sobre essas configurações, veja o manual do PHP:

* [error_reporting](http://php.net/errorfunc.configuration#ini.error-reporting)
* [display_errors](http://php.net/errorfunc.configuration#ini.display-errors)
* [display_startup_errors](http://php.net/errorfunc.configuration#ini.display-startup-errors)
* [log_errors](http://php.net/errorfunc.configuration#ini.log-errors)
