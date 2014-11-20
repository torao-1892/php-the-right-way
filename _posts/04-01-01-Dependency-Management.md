---
title: Gerenciamento de Dependência
anchor: gerenciamento_de_dependencia
---

# Gerenciamento de Dependência {#gerenciamento_de_dependencia_title}

Existem toneladas de bibliotecas PHP, frameworks, e componentes para você escolher. Seu projeto provavelmente irá usar 
muitos deles — eles são as dependências do projeto. Até recentemente, o PHP não possuía uma boa forma de gerenciar essas 
dependências de projeto. Mesmo se você as gerenciasse manualmente, ainda assim teria que se preocupar com autoloaders. 
Não mais.

Atualmente existem dois sistemas principais para gerenciamento de pacotes no PHP - o Composer e o PEAR. Qual deles é o 
certo para você? A resposta é: ambos.

 * Use o **Composer** quando estiver gerenciando as dependências de um único projeto.
 * Use o **PEAR** quando gerenciar dependências do PHP para o seu sistema inteiro.

Em geral, os pacotes Composer estarão disponíveis apenas em projetos que você especificar de forma explícita, enquanto
que um pacote PEAR estará disponível para todos os seus projetos PHP. Mesmo que o PEAR pareça ser o método mais fácil à 
primeira vista, existem vantagens em usar uma abordagem projeto-por-projeto para suas dependências.