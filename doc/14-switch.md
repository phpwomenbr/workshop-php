# Switch

A declaração switch é similar a uma série de declarações IF na mesma expressão. Em muitos casos, se deseja comparar as mesmas variáveis (ou expressões), com diferentes valores, e executar pedaços diferentes de código dependendo de qual valor ela é igual.

Exemplo:

```php
<?php

$idioma = "Português";

switch ($idioma) {
    case "Português";
        echo "Bem vindo";
        break;
    case "Inglês":
        echo "Welcome";
        break;
    case "Espanhol":
        echo "Bienvenido";
        break;
}
```

[Voltar a página inicial](../README.md)