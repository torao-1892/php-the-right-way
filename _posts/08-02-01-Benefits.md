---
isChild: true
title: Benefícios
anchor: templating_benefits
---

## Benefícios {#templating_benefits_title}

O principal benefício de se utilizar templates é a clara separação que eles criam entre a lógica de apresentação e o 
resto da sua aplicação. Templates têm a responsabilidade exclusiva de exibir o conteúdo formatado. Eles não são 
responsáveis por pesquisa de dados, persistência ou outras tarefas mais complexas. Isto leva a código mais limpo, mais 
legível que é especialmente útil em um ambiente de equipe, onde os desenvolvedores trabalham no código do lado do 
servidor (controladores, modelos) e designers trabalham no código do lado do cliente (markup).

Os templates também melhoram a organização do código de apresentação. Os templates são normalmente colocados em uma 
pasta "views", cada um definido dentro de um único arquivo. Essa abordagem incentiva a reutilização de código, onde 
grandes blocos de código são quebrados em pequenos pedaços reutilizáveis, chamados frequentemente de partials. Por 
exemplo, o cabeçalho e o rodapé do site de cada um pode ser definido como templates, que são então incluídos antes e 
depois de cada template de página.

Finalmente, dependendo da biblioteca que você usa, os templates podem oferecer mais segurança ao escapar automaticamente 
o conteúdo gerado pelo usuário. Algumas bibliotecas oferecem até mesmo sand-boxing, onde os criadores de templates só 
têm acesso à white-listed (lista branca) de variáveis e funções.
