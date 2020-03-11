# Estruturas condicionais

## If

O if é uma estrutura de controle que insere um desvio na execução natural do programa. Caso a condição do if seja satisfeita, o programa irá executar as instruções do seu bloco de comandos. Veja a seguir o exemplo:

```php
<?php

$a = 5;
$b = 2;

if ($a > $b) {
    echo "a é maior que b";
}
```
# Else

Caso a condição do if não seja satisfeita podemos utilizar o else. Veja o exemplo:

```php
<?php

$a = 1;
$b = 2;

if ($a > $b) {
    echo "a é maior que b";
} else {
    echo "a NÃO é maior que b";
}
``` 

Caso a condição do if não seja satisfeita utilizando o else, também podemos criar várias condições usando elseif. Elseif, como o nome sugere, é uma combinação do if e else. Entretanto, diferentemente do else, executará uma expressão alternativa somente se a expressão condicional do elseif for avaliada como TRUE.
Podemos ter vários elseif, porém só um else. Veja:

```php
<?php

$a = 5;
$b = 2;

if ($a > $b) {
    echo "a é maior que b";
} elseif ($a == $b) {
    echo "a é igual a b";
} else {
    echo "a é menor que b";
}
```

[Voltar a página inicial](../README.md)