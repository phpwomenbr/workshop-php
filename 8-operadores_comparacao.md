# Operadores de comparação

Operadores de comparação, como os seus nomes implicam, permitem que você compare dois valores. Veja a tabela abaixo os operadores de comparação disponíveis no PHP.

| Exemplo   |      Nome      |  Resultado |
|-------- |:-------------------|:--------|
| `$a == $b`     |  Igual        | Verdadeiro (TRUE) se $a é igual a $b.      |
| `$a === $b`      |   Idêntico      |   Verdadeiro (TRUE) se $a é igual a $b, e eles são do mesmo tipo.       |
| `$a != $b`      | Diferente                      | Verdadeiro se $a não é igual a $b.    |
| `$a <> $b`      | Diferente|   Verdadeiro se $a não é igual a $b.  |
| `$a < $b`      | Menor que |  Verdadeiro se $a é menor que $b.  |
| `$a > $b`      | Maior que |   Verdadeiro se $a é estritamente maior que $b.   |
| `$a <= $b`     | Menor ou igual |   Verdadeiro se $a é menor ou igual a $b.   |
| `$a >= $b`    | Maior ou igual 	 |   Verdadeiro se $a é maior ou igual a $b.   |

## Exemplos
```php
<?php
var_dump(0 == "0.0"); // 0 == 0 -> true
var_dump("1" == "01"); // 1 == 1 -> true
var_dump("10" < "3"); // 10 < 3 -> false
var_dump(100 >= "100"); // 100 >= 100 -> true
var_dump( 2 >= '2'); // 2 >= 100 -> true
var_dump( 'Olá, mundo' == 'Olá, Mundo'); // Olá, mundo == Olá, Mundo -> false
var_dump( 'Olá, mundo' == 'Olá, mundo'); // Olá, mundo == Olá, mundo -> true
```
