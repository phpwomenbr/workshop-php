# Tipos de dado

As variáveis e as constantes no PHP podem armazenar diversos tipos de dados e quem define qual é o tipo de dado é o PHP durante a execução do programa. Esse comportamento é chamado de **tipagem dinâmica**.

 O PHP suporta dez tipos primitivos.

Quatro tipos escalares:
- boolean (true ou false).
- integer (números inteiros).
- float (número de ponto flutuante, ou também double)
- string (texto que escrevemos entre aspas simples ou duplas).

Quatro tipos compostos:

- array
- object
- callable
- iterable

E finalmente dois tipos especiais:

- resource
- NULL

Neste workshop ensinaremos os tipos escalares. Para conhecer um pouco mais sobre os tipos de variáveis consulte a [Documentação do PHP](https://www.php.net).

Veja alguns exemplos:

```php
<?php

$vaiChover = true; //boolean
$idade = 27; //interger
$pi = 3.1415; //float
$meu_Nome = "Daiane"; //string
$array = [1,2,3]; //array 
```

> Nota: Para checar o tipo e valor de uma expressão, utilize a função var_dump().

[Voltar a página inicial](../README.md)
