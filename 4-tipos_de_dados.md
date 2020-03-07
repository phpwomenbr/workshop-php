# Tipos de dados 

O PHP suporta oito tipos de dados primitivos divididos em três grupos:

1.  Quatro tipos básicos, os dados escalares
    - integer (números inteiros)
    - float (número de ponto flutuante, ou também double)
    - string (texto que escrevemos entre aspas)
    - boolean (verdadeiro ou salso)
2.  Dois tipos compostos
    - array
    - object
    - callable
    - interable
3.  Dois tipos especiais:
    - resource
    - NULL
## Exemplo de dados escalares:
 ```php
<?php
$inteiro = 23; // inteiro
$float = 4.50; //float
$string = 'Olá, mundo!'; //string
$boleeano = TRUE; // boleano
``` 

Para saber o tipo de uma variável podemos utilizar a função [`gettype`](https://www.php.net/manual/en/function.gettype) ou a função [`var_dump`](https://php.net/var_dump). No exemplo a seguir utilizaremos a função `gettype`: 
```php
echo gettype($boleano); // imprime na tela: boolean
echo gettype($string); // imprime na tela: string
```
