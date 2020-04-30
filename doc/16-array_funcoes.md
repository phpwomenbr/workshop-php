# Funções para manipular arrays

No manual do PHP, exitem 81 funções diferentes para trabalhar com array. Escolhemos algumas mais comumente usadas para apresentar aqui.

## array_diff

Identifica a diferença entre arrays

```php
array_diff ( array $array1 , array $array2 [, array $... ] ) : array
``` 

Compara o `array1` com um ou mais arrays e retorna os valores do `array1` que não estão presentes em nenhum dos outros arrays.

**Parâmetros** 

- `array1`: O array para comparar

- `array2`: Um array para comparar
 
- `...`: Mais arrays para comparar 


Veja o exemplo:

```php
<?php
$array1 = array("a" => "verde", "vermelho", "azul", "vermelho");
$array2 = array("b" => "verde", "amarelo", "vermelho");
$result = array_diff($array1, $array2);

print_r($result);
``` 
Isto irá mostrar: 

    Array
    (
    [1] => azul
    )


## array_keys

Esta função retorna todas as chaves de um array desde que sejam dos tipos: numérica ou string.

```php
array_keys ( array $array ) : array
``` 

Podemos também especificar um valor para a função retornar sua chave correspondente.

```php
array_keys ( array $array , mixed $search_value [, bool $strict = FALSE ] ) : array
``` 

**Parâmetros** 

- `array`: Um array contendo chaves a serem retornadas. 

- `search_value`: Se especificado, então somente chaves contendo estes valores são retornadas. 
 
- `strict`: Determina se a comparação deve ser rígida (===) ou seja, se vai verificar se são do mesmo tipo também. 

Veja os exemplos:

```php
<?php
$array = array(0 => 100, "cor" => "vermelho");
print_r(array_keys($array));

$array = array("azul", "vermelho", "verde", "azul", "azul");
print_r(array_keys($array, "azul"));

$array = array("1", 1, 1, 1, "1");
print_r(array_keys($array, "1","==="));
```

O exemplo acima irá imprimir:

    Array
    (
        [0] => 0
        [1] => cor
    )
    Array
    (
        [0] => 0
        [1] => 3
        [2] => 4
    )
    Array
    (
        [0] => 0
        [1] => 4
    )

## array_key_exists

Verifica a existência de uma chave no array. Retorns true em caso positivo e false em caso negativo. 

```php
array_key_exists ( mixed $key , array $array ) : bool
``` 

**Parâmetros** 

- `key`: Valor para verificar.

- `array`: Um array com chaves para verificar.
 
Exemplo:
```php
<?php
$busca_array = array("primeiro" => 1, "segundo" => 4);
if (array_key_exists("primeiro", $busca_array)) {
    echo "O elemento 'primeiro' está no array!";
}
```

**OBS:** A função `isset()` também pode ser utilizada para verificar a existência de uma chave porém, não retorna `TRUE` para valores de chave que correspondam a um valor NULL, enquanto que `array_key_exists()` retorna. 

## in_array

Checa se um valor existe em um array. Retorna **TRUE** em caso positivo e **FALSE** em caso negativo.

```php
in_array ( mixed $needle , array $haystack [, bool $strict ] ) : bool
```

**Parâmetros** 

- `needle`: O valor procurado.

- `haystack`: O array

-  `strict:` Determina se a comparação deve ser rígida, ou seja, se vai verificar se são do mesmo tipo também

Exemplo:
```php
<?php
$os = array("Mac", "NT", "Irix", "Linux"); 
if (in_array("Irix", $os)) { 
    echo "Tem Irix";
}
if (in_array("mac", $os)) { 
    echo "Tem mac";
}
```
A segunda condicional falha pois in_array() diferencia letras minúsculas e maiúsculas. Então, a saída seria:

    Tem Irix


Agora com checagem de tipos

```php
<?php
$a = array('1.10', 12.4, 1.13);

if (in_array('12.4', $a, true)) {
    echo "'12.4' encontrado com checagem de tipo\n";
}
if (in_array(1.13, $a, true)) {
    echo "1.13 encontrado com checagem de tipo\n";
}
```

O exemplo acima irá imprimir:

    1.13 encontrado com checagem de tipo

## array_pop

Extrai o último elemento do array.

```php
 array_pop ( array &$array ) : mixed
```

    Nota: Esta função irá resetar() o ponteiro do array depois do uso.

**Parâmetros** 

- `array:` O array para obter os valores.

Exemplo:

```php
<?php
$cesta = array("laranja", "banana", "melancia", "morango");
$fruta = array_pop($cesta);
print_r($cesta);
?>
```

O exemplo acima irá imprimir:

    Array
    (
        [0] => laranja
        [1] => banana
        [2] => melancia
    )
 e morango será passado para $fruta. 