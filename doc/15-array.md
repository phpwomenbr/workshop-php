# Array

Um array no PHP é na verdade um mapa ordenado. Um mapa é um tipo que relaciona valores a chaves. Este tipo pode ser usado de várias formas: ele pode ser tratado como um array, uma lista (vetor), dicionário, coleção, pilha, fila e etc. Assim como existe a possibilidade dos valores do array serem outros arrays, árvores e arrays multidimensionais.

## Especificando um Array

Um array pode ser criado usando o construtor de linguagem array(). Ele recebe como argumento qualquer quantidade de pares (chave => valor) separados por vírgula. 

```php
$array = [
    "carros" => "Gol",
    "animal" => "Gato",
];
```

A chave pode ser tanto inteiro como uma string.

Além disso os seguintes tipos de chaves podem ocorrer.

- **Strings** contendo inteiros válidos, serão convertidos para o tipo inteiro. Por exemplo, a chave"8" será, na verdade, armazenada como 8. Entretanto, "08" não será convertido, por não ser um inteiro decimal válido.
- **Floats** também são convertidos para inteiros, isso significa que a parte fracionada será removida. Por exemplo, a chave 8.7 será na verdade armazenada como 8.
- **Booleanos** são convertidos para inteiros, igualmente, por exemplo, a chave true, será na verdade armazenada como 1 e a chave false como 0.
- **Null** será convertido para uma string vazia, por exemplo, a chave null na verdade será armazenada como "".
- **Arrays** e objetos não podem ser usados como chaves. Fazer isso resultará em um aviso: `Illegal offset type`.

Se vários elementos na declaração do array utilizam a mesma chave, apenas o último será utilizado, enquanto todos os outros serão sobrescritos. 

```php
<?php
$array = [
    1    => "a",
    "1"  => "b",
    1.5  => "c",
    true => "d",
];
var_dump($array);
```
O exemplo acima irá imprimir:
```php
array(1) {
  [1]=>
  string(1) "d"
}
```
Como todas as chaves do exemplo acima foram convertidas para 1, o valor será sobrescrito a cada novo elemento e o valor final atribuído "d", será o único que restará.

## Misturando inteiro e string
As chaves dos arrays no PHP podem conter, ao mesmo tempo, inteiro e string, por que o PHP não faz distinção entre arrays indexados e associativos.

```php
<?php
$array = [
    "carro" => "Gol",
    "animal" => "Gato",
    100   => -100,
    -100  => 100,
];
var_dump($array);
```
O exemplo acima irá imprimir:

```php
array(4) {
  ["carro"]=>
  string(3) "Gol"
  ["animal"]=>
  string(4) "Gato"
  [100]=>
  int(-100)
  [-100]=>
  int(100)
}
```
A chave é opcional. Se não for especificada, o PHP utilizará o incremento da chave do tipo inteiro com maior valor utilizado.

## Arrays indexados sem chaves

```php
<?php
$array = ["banana", "maçã", "hello", "world"];
var_dump($array);
```

O exemplo acima irá imprimir:
```php
array(4) {
  [0]=>
  string(6) "banana"
  [1]=>
  string(4) "maçã"
  [2]=>
  string(5) "hello"
  [3]=>
  string(5) "world"
}
```
## Chaves em alguns elementos

É possível especificar a chave somente para alguns elementos e omití-las para outros: 
```php
<?php
$array = [
         "a",
         "b",
    6 => "c",
         "d",
];
var_dump($array);
```

O exemplo acima irá imprimir:

```php 
array(4) {
  [0]=>
  string(1) "a"
  [1]=>
  string(1) "b"
  [6]=>
  string(1) "c"
  [7]=>
  string(1) "d"
}
```
Como pode ver, o último valor "d" foi atribuído a chave 7. Isso acontece porque a chave com maior inteiro antes dela era 6.

## Acessando elementos do array

Elementos do array podem ser acessados utilizando a sintaxe `array[chave]`.
```php
<?php
$array = [
    "foo" => "bar",
    42    => 24,
    "multi" => array(
         "dimensional" => array(
             "array" => "foo"
         )
    )
];


var_dump($array["foo"]);
var_dump($array[42]);
var_dump($array["multi"]["dimensional"]["array"]);
```

O exemplo acima irá imprimir:
```php
string(3) "bar"
int(24)
string(3) "foo"
```
Nota:
Tanto colchetes quanto chaves podem ser utilizados para acessar elementos de um array (por exemplo, `$array[42]` e `$array{42}` irão fazer a mesma coisa que o exemplo anterior).

## Criando/modificando com a sintaxe de colchetes 

Você pode modificar um array existente atribuindo valores a ele.

```php
$arr[chave] = valor;
$arr[] = valor;
// chave pode ser tanto um integer quanto uma string
// valor pode ser qualquer valor de qualquer tipo
```
Se ainda $arr não existir, será criado, servindo como alternativa para criação de um array. 

Para mudar um certo valor, apenas atribua um novo valor para um elemento especificado por sua chave. Se você quiser remover um par chave/valor, você precisa aplicar a função unset() nele.
```php
<?php
$arr = array(5 => 1, 12 => 2);

$arr[] = 56;    // Isto é o mesmo que $arr[13] = 56;
                // nesse ponto do script

$arr["x"] = 42; // Isto acrescenta um novo elemento
                // para o array com a chave "x"

unset($arr[5]); // Isto remove um elemento do array

unset($arr);    // E isto apaga todo o array
```
## Como percorrer um array

O construtor foreach fornece uma maneira fácil de iterar sobre arrays. O foreach funciona somente em arrays e objetos. Possui duas sintaxes:

```php
foreach (array_expression as $value)
    statement
foreach (array_expression as $key => $value)
    statement
```

A primeira forma, itera sobre o array trazendo somente o valor e a segunda tras a chave e o valor.

Para modificar diretamente elementos de um array dentro de um laço atribua um novo valor a cada iteração.

```php
<?php
$arr = [1, 2, 3, 4];
foreach ($arr as $key => $value) {
    $arr[$key] = $value * 2;
}
var_dump($arr);
// $arr is now array(2, 4, 6, 8)