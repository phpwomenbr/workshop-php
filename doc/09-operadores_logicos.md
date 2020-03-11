# Operadores lógicos

Foi criado por GeorgeBoole(1815-1864), são a base dos computadores digitais e permitem combinar ou excluir termos, como palavras-chave levando a resultados mais precisos em buscas.

A seguir a tabela de operadores lógicos:

| Exemplo   |      Nome      |  Resultado |
|-------- |:-------------------|:--------|
| `$a and $b`     |  E        | Verdadeiro (TRUE) se tanto $a quanto $b são verdadeiros.      |
| `$a or $b`     |  OU       | Verdadeiro se $a ou $b são verdadeiros.      |
| `$a xor $b`      |   XOR      |  Verdadeiro se $a ou $b são verdadeiros, mas não ambos.       |
| `! $a`     | NÃO                      | Verdadeiro se $a não é verdadeiro.   |
| `$a && $b`      | E|   Verdadeiro se tanto $a quanto $b são verdadeiros.  |
| <code>$a &#124;&#124; $b</code>    | OU|  Verdadeiro se $a ou $b são verdadeiros. |

Exemplo

```php
<?php

$a = true;
$b = false;


$j = ($a && $b);
$k = ($a || $b);
$l = ($a and $b);
$m = ($a  or  $b);

var_dump($j); //false
var_dump($k); //true
var_dump($l); //false
var_dump($m); //true


[Voltar a página inicial](../README.md)