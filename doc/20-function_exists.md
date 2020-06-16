# Function_exists

A `function_exists` - retorna `TRUE` se a função dada está definida, do contrário, `FALSE`.

## Sintaxe

```php 
 function_exists( string $function_name ) : bool
```


## Exemplo
```php
// declaração da function mensagem 
function mensagem() 
{ 
    echo "Olá, mundo!"; 
} 
// verificando se a function mensagem existe 
if (function_exists('mensagem')) {
    echo "mensagem() function está disponível" . PHP_EOL; 
} else {
    echo "mensagem() function não está disponível" . PHP_EOL; 
}
```

Agora vamos imaginar que você tenha um arquivo separado com algumas funções e deseja verificar se a função procurada existe. Primeiro você deve fazer um include ou require para fazer a referência de onde se vai buscar aquela função. Em seguida, você pode verificar se a função a ser procurada existe.

Veja o exemplo:

```php
require 'functions.php';

// verificando se a function mensagem existe 
if (function_exists('divide')) {
    echo "mensagem() function está disponível" . PHP_EOL; 
} else {
    echo "mensagem() function não está disponível" . PHP_EOL; 
}
```

[Voltar a página inicial](../README.md)