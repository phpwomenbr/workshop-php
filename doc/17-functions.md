# Functions

Uma função é um bloco de código identificado por um nome, que executa uma tarefa específica e que pode ser referenciada a partir de várias partes do código. Um exemplo bastante conhecido de função é na própria matemática. Vamos relembrar...

```
f(x) = x * 2
f(3) = 3 * 2 = 6
```

Imagine que você está trabalhando num sistema em que é necessário multiplicar dois números. Caso essa operação seja realizada repetidas vezes dentro código, então ela pode ser implementada dentro de uma função que será invocada sempre que for necessário realizar a multiplicação.

Além disso, você pode utilizar `functions` para realizar diversos tipos de operações como por exemplo:

- Somar dois números,
- Verificar se é um CPF está correto
- Verificar se um valor de uma variável é válido
- Transformar letras maiúsculas em minúsculas...

## Sintaxe

A declaração de funções no PHP é feita a partir da palavra reservada `function`, seguida do nome da função e de sua **lista de argumentos**, enquanto o corpo da função é delimitado por chaves `{ }`, entre as quais ficarão as instruções a serem executadas quando a função for invocada.

```php
function nomeFuncao($arg1, $arg2, $arg3, ... $argN)
{
    // instruções
} 
```
- Um função é declarada pela palavra reservada `function` seguida do nome da função.
- Para nomear uma função podemos usar qualquer sequência de caracteres que comece com uma letra ou traço baixo `_`.

> O PHP não diferencia letras maiúsculas de minúsculas para o nome de funções, ou seja, você pode chamar a função com o nome dela com letras em maiúsculo ou minúsculo que será reconhecida como a mesma função.
>> Por convenção, as funções no PHP são nomeadas com letras **minúsculas**.

## Criando uma `function`

```php
function multiplica_valores($valor1, $valor2)
{
   $multiplica = $valor1 * $valor2;
   return $multiplica;
}
echo multiplica_valores(4, 3); // saída: 12
```

* Neste exemplo estamos criando uma function `multiplica_valores`.
* Ela possui 2 argumentos (ou parâmetros) `$valor1` e `$valor2`.
* Entre as chaves `{ }`estamos declarando uma variável `$multiplica` que está recebendo a multiplicação das variáveis: `$valor1 * $valor2`.
* Por último, estamos executando a função `multiplica_valores` passando os números 4 e 3 como argumentos e imprimindo o retorno desta função.

Se executarmos este trecho de código teremos como saída o valor 12.

### Argumentos de funções

Informações podem ser passadas para funções através da lista de argumentos, que é uma lista de expressões delimitados por vírgulas. Esses argumentos são avaliados da esquerda para a direita.
O PHP suporta a passagem de **argumentos por valor**, **passagem por referência** e **valores padrões** de argumentos.

Lista de argumentos de tamanho variável (array) também são suportadas. Veja o exemplo:

```php
<?php
function soma(array $input)
{
    return "$input[0] + $input[1] = ", $input[0]+$input[1];
}

echo soma([1, 2]); // saída: 1 + 2 = 3
```

#### Passagem de parâmetros por valor

Quando passamos uma variável como parâmetro em uma função, todas as alterações nelas que ocorrerem dentro da função são serão refletidas fora da função.

Isso é chamado de processo de passagem de parâmetros por valor, já que apenas o valor é passado para uso na função. Veja este exemplo:

```php
/**
 * Declaração da função soma 
 * e os parâmetros $num1 e $num2
 **/
function soma($num1, $num2)
{
    $total = $num1 + $num2;
    return $total;
}

// definindo os valores para as variáveis
echo soma(2, 3);
```

Após a declaração da função foi passado os valores 2 e 3 para os parâmetros `$num1` e `$num2`, respectivamente. Ao executar a função será retornado e impresso o valor da soma com o valores definidos.

#### Passagem de parâmetros por referência

Quando queremos que variável usada no argumento sofra as alterações internas da função usamos a passagem de parâmetros por referência. Para usar o parâmetro por referência, bastar usar o símbolo `&` antes da variável. Exemplo:

```php
//Criada a referência em $num1
function referencia(&$num1)
{
    $num1 *= 5;

    //retorno o valor de $num1 * 5
    return $num1;
}
$num2 = 3;
//Execução da função
referencia($num2);
echo $num2;
```

* Note que foi criada uma **referência** em `$num1` que irá receber o valor de `$num2`.
* Em seguida o valor de `$num1` é alterado pela operação de atribuição.
* Na próxima linha é retornado o valor final de `$num1`.
* Abaixo a função é executada passando como referência a variável `$num2` para a variável `$num_`.
* E por último é impresso o valor 15 com final da execução da função.

#### Passagem de parâmetros por valor padrão

Essa forma de passagem de argumentos consiste em definir no momento da declaração da função quais serão os valores dos seus parâmetros. Veja o exemplo:

```php
/**
 * Declaração da função passagem_padrao
 * e do parâmetro $num1 já com seu valor definido
 **/
function passagem_padrao($num1 = 15)
{
    return $num1;
}

//Será impresso o retorno da função - 15
echo passagem_padrao();
```

* O parâmetro `$num1` é declarado com valor 15.
* Em seguida `*$num1` será o valor de retorno da função.
* Ao executar a função o valor definido ao parâmetro será retornado e impresso.

Veremos agora outro exemplo de aplicação de parâmetros por valor padrão.

```php
<?php

function capital($capital, $estado = 'Um estado brasileiro')
{
   return "$estado, capital: $capital" . PHP_EOL;
}
echo capital('Natal', 'RN');
echo capital('Belo Horizonte', 'MG');
echo capital('Goiânia');
/* saída:
RN, capital: Natal
MG, capital: Belo Horizonte
Um estado brasileiro, capital: Goiânia
*/
```
Caso não seja colocado nenhum argumento, o valor padrão será assumido, como na última linha do exemplo.

Os valores padrão devem ser sempre os últimos para que o PHP interprete primeiro os parâmetros sem valor-padrão e assim evitar erros.

### Retorno de funções
Ao escrever uma função é necessário especificar se ela retornará um valor ou não.

Como exemplo vamos criar uma função chamada `dividir` que realiza a divisão entre duas variáveis e retornar o resultado dessa operação.

```php 
function dividir($num1, $num2)
{
    $operacao = $num_1 / $num_2;

    return $operacao;
}
```
Veja que não é retornado um valor com a execução da função, mas sim impresso o valor da divisão entre as variáveis.

Para que seja possível que a função `dividir()` retorne algum valor é necessário alterá-la inserindo a instrução `return` no lugar da palavra `echo.

> Veremos mais a frente o retorno de funções de forma mais detalhada.

## Funções recursivas

Recursividade - Este nome é dado quando ocorre uma chamada de determinada função a ela mesma.
Um exemplo bastante conhecido é a função de cálculo do fatorial de um número.

Veja o exemplo a seguir:

```php
function recursion($a)
{
    if ($a < 20) {
        echo $a . PHP_EOL;
        recursion($a + 1);
    }
}

recursion(1); // saída: 1 até 19
```
Outro exemplo clássico de função recursiva é o cálculo do fatorial.
Fatorial de um número n é multiplicação dele mesmo por todos os seus antecessores. Por convenção, o fatorial de 0 é 1. Veja o exemplo:

```php
<?php

function fatorial($numero)
{
    if($numero<0) { 
        return -1;
    }
    if($numero<=1) {
        return 1;
    }
    return $numero*fatorial($numero-1);
}
echo "O fatorial de 3 é " . fatorial(3) . PHP_EOL;
echo "O fatorial de 4 é " . fatorial(4) . PHP_EOL;
echo "O fatorial de 5 é " . fatorial(5) . PHP_EOL;
```
## Declarações de tipo
Declarações de tipo permitem que funções requiram que parâmetros sejam de certos tipos ao chamá-los. 

Se o valor informado no parâmetro tiver um tipo incorreto então um erro é gerado.

Para declarar o tipo o seu nome deve ser adicionado antes no nome do parâmetro.
Veja o exemplo:

```php
function salarioAReceber(string $nome, float $salario): string
{
    return $nome . " " . $salario;
}

echo salarioAReceber("Joana", 1000) . PHP_EOL;
```

[Voltar a página inicial](../README.md)