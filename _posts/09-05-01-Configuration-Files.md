---
title: Arquivos de Configuração
isChild: true
anchor: arquivos_de_configuracao
---

## Arquivos de Configuração {#arquivos_de_configuracao_title}

Quando criar arquivos de configuração para suas aplicações, as melhores práticas recomendam que um dos seguintes métodos
seja seguido:

- É recomendado que você armazene sua informação de configuração onde ela não possa ser acessada diretamente ou puxada
através do sistema de arquivos.
- Se você tiver que armazenar seus arquivos de configuração no diretório raiz, nomeie os arquivos com a extensão `.php`.
Isso garante que, mesmo se um script for acessado diretamente, ele não será mostrado como texto puro.
- As informações nos arquivos de configuração devem ser adequadamente protegidas, ou através de criptografia ou por
permissões de grupos/usuários no sistema de arquivos
