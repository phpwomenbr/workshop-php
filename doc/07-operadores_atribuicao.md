 # Operadores de atribuição
 
 O operador básico de atribuição é "=". A sua primeira inclinação deve ser a de pensar nisto como "é igual". Não! Isto quer dizer, na verdade, que o operando da esquerda recebe o valor da expressão da direita (ou seja, "é definido para").

O valor de uma expressão de atribuição é o valor atribuído. Ou seja, o valor de "$a = 3" é 3. Isto permite que você faça alguns truques:

```php

<?php

$a = ($b = 4) + 5; // $a é igual a 9 agora e $b foi definido como 4.
```

Além do operador básico de atribuição, há "operadores combinados" para todos os operadores aritméticos, de array e string que permitem a você pegar um valor de uma expressão e então usar seu próprio valor para o resultado daquela expressão. Por exemplo:

```php
<?php

$a = 3;
$a += 5; // define $a para 8, como se disséssemos: $a = $a + 5;
```

[Voltar a página inicial](../README.md)
