---
isChild: true
---

## Relatório de Erros

O registro de erros pode ser útil para encontrar pontos problemáticos em sua aplicação, mas isso também pode expor informações sobre
a estrutura de sua aplicação para o mundo exterior. Para proteger efetivamente sua aplicação dos problemas que poderiam
ser causados com a exposição dessas mensagens, você precisa configurar seu servidor de formas diferentes quando em desenvolvimento versus quando em produção (no ar).

### Desenvolvimento

Para mostrar erros no seus ambiente de <strong>desenvolvimento</strong>, configure as definições a seguir no seu `php.ini`:

- display_errors: On
- error_reporting: E_ALL
- log_errors: On

### Produção

Para esconder os erros no seu ambiente de <strong>produção</strong>, configure seu `php.ini` assim:

- display_errors: Off
- error_reporting: E_ALL
- log_errors: On

Com essas configurações em produção, os erros continuarão sendo registrados nos logs de erros do servidor web, mas eles não serão
mostrados para o usuário. Para mais informações sobre essas configurações, veja o manual do PHP:

* [Error_reporting](http://www.php.net/manual/en/errorfunc.configuration.php#ini.error-reporting)
* [Display_errors](http://www.php.net/manual/en/errorfunc.configuration.php#ini.display-errors)
* [Log_errors](http://www.php.net/manual/en/errorfunc.configuration.php#ini.log-errors)