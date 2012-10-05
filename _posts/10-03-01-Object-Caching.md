---
isChild: true
---

## Cache de Objetos

Existem momentos onde pode ser benéfico fazer cache de objetos individuais no seu código, como em dados que são custosos
de conseguir ou em chamadas de bancos de dados cujo resultado dificilmente se modifica. Você pode usar um software de cache de objetos para armazenar esses
pedaços de dados na memória, para acessá-los posteriomente de forma extremamente rápida. Se você guardar esses itens em um data store logo que os recuperar,
e depois os enviar diretamente do cache para as suas requisições posteriores, você conseguirá uma melhora significativa no desempenho além de reduzir a carga nos seus servidores de banco de dados.

Muitas das soluções populares de cache de bytecode permitem que você também faça cache de dados personalizados, assim há ainda mais razões para se
beneficiar deles. Tanto o APC, quanto o XCache e o Wincache fornecem APIs para armazenar dados do seu código PHP na memória cache deles.

Os sistemas mais usados para cache de objetos em memória são o APC e o memcached. O APC é uma escolha excelente para
cache de objetos, ele inclui uma API simples para adicionar seus próprios dados para seu cache de memória e é muito fácil de configurar e utilizar. A
única limitação real do APC é que ele fica amarrado ao servidor onde ele está instalado. O memcached por outro lado é instalado
como um serviço separado e pode ser acessado através da rede, assim você pode armazenar objetos em um data store
ultra-rápido, em uma localização central, e vários sistemas diferentes podem acessá-lo.



In a networked configuration APC will usually outperform memcached in terms of access speed, but memcached will be able
to scale up faster and further. If you do not expect to have multiple servers running your application, or do not need
the extra features that memcached offers then APC is probably your best choice for object caching.

Example logic using APC:

{% highlight php %}
<?php
// check if there is data saved as 'expensive_data' in cache
$data = apc_fetch('expensive_data');
if (!$data)
{
    // data not in cache, do expensive call and save for later use
    $data = get_expensive_data();
    apc_store('expensive_data', $data);
}

print_r($data);
{% endhighlight %}

Learn more about popular object caching systems:

* [APC Functions](http://php.net/manual/en/ref.apc.php)
* [Memcached](http://memcached.org/)
* [Redis](http://redis.io/)
* [XCache APIs](http://xcache.lighttpd.net/wiki/XcacheApi)
* [WinCache Functions](http://www.php.net/manual/en/ref.wincache.php)
