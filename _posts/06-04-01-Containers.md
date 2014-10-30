---
title: Containers
isChild: true
anchor: containers
---

## Containers {#containers_title}

A primeira coisa que você deve entender sobre os Containers da Dependency Injection é que eles não são a mesma coisa
que ela. Um container é um utilitário de conveniência que nos ajuda implementar a Dedepency Injection, no entanto, eles
podem ser, e muitas vezes são, uma implementação anti-pattern, Service Location (Serviço de Localização).
Injetar um container DI como um Localizador de Serviço para suas classes, sem dúvida, cria uma dependência difícil de
substituir no container. Isso também torna seu código menos transparente e, finalmente, mais difícil de testar.

A maioria dos frameworks têm seu próprio Container de Dependency Injection que permite ligar suas dependências em
conjunto, através de configuração.
O que isto significa, na prática, que você pode escrever o código da aplicação tão limpo e desacoplado como do framework
foi construído.
