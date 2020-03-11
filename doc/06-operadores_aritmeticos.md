# Operadores

Os operadores são utilizados para manipular os dados ou expressões em um programa. 
Podemos ter operadores aritméticos, atribuição, comparação entre outros. Para conferir todos os tipos de operadores disponíveis no php consulte o [Manual do PHP](https://www.php.net/manual/pt_BR/language.operators.php).

## Operadores aritméticos

Todo mundo já usou operadores aritméticos na escola! Nos primeiros anos de estudo aprendemos a fazer contas de soma, subtração, multiplicação e divisão. Em php eles também são simples e têm a mesma simbologia em todas as linguagens de programação ( +, -, * e / ).

Além desses mais simples, tem outro que não recebe muita atenção e pode ser que você não o conhece que é o módulo (%). Ele serve para calcular o resto da divisão de um número.

### Exemplo módulo

```php
<php?
$x = 5;
$y = 3;
$expressao = $x % $y;

echo $expressao;
```
Deste modo temos como resultado o número 2 que é o resto da divisão de 5 por 3.

Nota: Se você quer verificar se um número é par ou ímpar, pode utilizar o float.

## Precedência de operadores

Assim como na matemática devem obedecer uma ordem de precedência. Veja a tabela abaixo:

| Ordem   |      Operação      |  Símbolo |
|-------- |:-------------------|:--------:|
| 1ª      |  Parênteses        | ( )      |
| 2ª      |   Potenciação      |  **      |
| 3ª      | Multiplicação, Divisão e Módulo(resto da divisão)                       | *, /, %,    |
| 4ª      | Adição e Subtração |   +, -   |

A precedência de um operador especifica quem tem mais prioridade quando há duas delas juntas. Por exemplo, na expressão 1 + 5 * 3, a resposta é 16 e não 18 porque o operador de multiplicação ("*") tem prioridade de precedência que o operador de adição ("+"). Parênteses podem ser utilizados para forçar a precedência, se necessário. Assim, (1 + 5) * 3 é avaliado como 18.

Quando operadores tem precedência igual a associatividade decide como os operadores são agrupados. Por exemplo "-" é associado à esquerda, de forma que 1 - 2 - 3 é agrupado como (1 - 2) - 3 e resulta em -4.

## Exemplo

```php
<?php

$x = 5;
$y = 3;
$z = 2;

$expressao = $x + ($y ** $z) / $z; // 5 + 9 / 2; 5 + 4.5 ; 9.5

echo $expressao;
```

Será exibido na tela o resultado 9.5

[Voltar a página inicial](../README.md)