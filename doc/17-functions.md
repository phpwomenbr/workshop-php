# Functions

Uma função é um bloco de código identificado por um nome, que executa uma tarefa específica.
A função pode ser referenciada a partir de várias partes do código. Será a chamada da função.

Vantagens:
- reutilização de código
- código mais "limpo"
- código mais organizado

A declaração de funções no PHP é feita a partir da palavra reservada `function`, seguida do nome da função e de sua lista de argumentos, enquanto o corpo da função é delimitado por chaves `{ }`, entre as quais ficarão as instruções a serem executadas quando a função for invocada.

```php
<?php
function nomeFuncao($par1, $par2, $par3, ..., $parN){
  echo "Exemplo de função.\n";
  return $valor;
}
?>
```

- A palavra reservada `function` define o bloco de código como uma função.
- O `nomeFuncao` deve ser um nome de fácil entendimento para identificação da função.
- Assim como as variáveis, as funções não podem ser iniciadas com números ou caracteres especiais, exceto o underline `(_)`.
- Trabalhando em paradigma de orientação a objetos, inicia-se o nome da função com letra minúscula por convenção.
- Os valores entre parênteses são chamados de **parâmetros** ou **argumentos** e são valores dos quais a função depende para ser executada corretamente.
- As funções podem ser classificadas quanto ao seu retorno como vazias (void) ou com retorno. Veremos mais detalhadamente abaixo.

> Nem sempre os parâmetros são necessários, então pode-se omiti-los na definição da função, mantendo apenas os parênteses.

As funções **void** ou **sem retorno** apenas executam uma série de comandos sem a obrigação de devolver um valor específico como resultado. Já as funções **com retorno**, ao serem executadas, resultam diretamente em um dado valor que, no PHP, não tem tipo de dado definido.

## Função sem parâmetro e sem retorno

```php
function exibirMensagem() {
    echo "Olá" . PHP_EOL;
    echo "Seja Bem Vindo(a)!"
}
```

## Função com parâmetro e sem retorno:

```php
function exibirMensagem($nome) {
    echo "Olá" . PHP_EOL;
    echo $nome;
}
```

## Chamando uma função sem retorno:

```php
<?php
    //definição da função
   function exibirMensagem($nome) {
      echo "Olá" . PHP_EOL;
      echo $nome;
   }

   //chamando a função
   exibirMensagem("PHPWomenBR");
?>
```

## Função sem parâmetro e com retorno:

```php
<?php    
   //definição da função    
   function exibirMensagem() {
      echo "Olá" . PHP_EOL;
  	   echo "PHPWomenBR";
   }         
 
   //chamando a função    
   exibirMensagem();
?>
```

## Função com parâmetro e com retorno

```php
<?php     
   //definição da função     
   function somar($numA, $numB)   {
      return $numA + $numB;
   }       
   
   $resultado = somar(1,2);     
   echo $resultado; 
?>
```

## Funções recursivas

### Recursividade
Este nome é dado quando ocorre uma chamada de determinada função a ela mesma.
Um exemplo bastante conhecido é a função de cálculo do fatorial de um número.

Veja o exemplo a seguir:

```php
<?php
  $num = 3;
  $fat = 1;
    
  for($i=1; $i<=$num ; $i++)
  $fat = $fat * $i;
   
  echo $fat;
```

> Dica: Poderíamos substituir a linha `$fat = $fat * $i;` por `$fat *= $i;`.


[Voltar a página inicial](../README.md)