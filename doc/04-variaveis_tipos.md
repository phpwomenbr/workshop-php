# Tipos de dados 

Em PHP temos dez tipos de dados primitivos:
- integer (números inteiros)
- float (número de ponto flutuante, ou também double)
- string (texto que escrevemos entre aspas)
- boolean (verdadeiro ou falso)

- array
- object
- callable
- interable

- resource
- NULL
    
## Exemplo de variáveis:
 ```php
<?php
$inteiro = 23; // inteiro
$float = 4.50; //float
$string = 'Olá, mundo!'; //string
$boleeano = TRUE; // boleano
``` 

Para saber o tipo de uma variável podemos utilizar a função [`gettype`](https://www.php.net/manual/en/function.gettype) ou a função [`var_dump`](https://php.net/var_dump). No exemplo a seguir utilizaremos a função `gettype`: 
```php
echo gettype($inteiro) . PHP_EOL; // imprime na tela integer
echo gettype($float) . PHP_EOL; // imprime na tela double
echo gettype($string). PHP_EOL;// imprime na tela string
echo gettype($boleeano) . PHP_EOL; // imprime na tela boolean
```
Nota: No exemplo acima utilizamos a constante `PHP_EOL` para dar quebra de linha.

Outra forma de visualizar tipo de uma variável é utilizando a função `var_dump`. Esta função pode ser utilizada para debugar código. Ele retorna o tipo e o valor de uma variável.

Veja o exemplo:
```php
var_dump($inteiro);
var_dump($float);
var_dump($string);
var_dump($boleeano);
```
Repare que não é necessário utilizar a palavra reservada `echo` e nem utilizar constante para quebrar linha.
O resultado na tela seria este:
```php
int(23)
float(4.5)
string(12) "Olá, mundo!"
bool(true)
```

[Voltar a página inicial](../README.md)
