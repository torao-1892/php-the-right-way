---
isChild: true
---

## Hash de Senhas com Bcrypt {#password_hashing_with_bcrypt_title}

No fim, todos construímos aplicações PHP que dependem de login dos usuários. Usuários e senhas (com hash) são
armazenadas em um banco de dados e posteriormente são usados para autenticar os usuários no login.

É importante que você faça adequadamente o _hash_ das senhas que são armazenadas em um banco de dados. Se as senhas
não estiverm com hash, e seu banco for hackeado ou acessado por alguém não autorizado, todas as contas dos usuários
ficarão comprometidas.

**Faça o hash das senhas com o Bcrypt**. É super simples, e (para todos os efeitos) o Bcrypt impossibilita que alguém
possa, usando engenharia reversa em uma versão em texto puro de uma senha, fazer com que o banco fique comprometido.

Existem várias bibliotecas Bcrypt para o PHP que você pode utilizar.

* [Leia "Como Armazenar uma Senha de Forma Segura" por Coda Hale][3]
* [Use o Bcrypt com o PHPass][4]

[3]: http://codahale.com/how-to-safely-store-a-password/
[4]: http://www.openwall.com/phpass/
