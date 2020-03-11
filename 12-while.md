# While
O while é uma estrutura de repetição que possui uma condição para poder ser executada. Ele estabelece um laço de repetição do seu bloco de comandos, até que a condição seja satisfeita. 
No exemplo a seguir estamos imprimindo de 1 até 10.

## Exemplo 1
```php
<?php

$i = 1;
while ($i <= 10) {
    echo $i++ . PHP_EOL;
}
```
Neste segundo exemplo temos o mesmo programa com uma pequena mudança. Veja:

## Exemplo 2

```php
<?php
$i = 1;
while ($i <= 10) {
    echo $i . PHP_EOL;
    $i++;
}
```


