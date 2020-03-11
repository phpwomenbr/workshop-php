# For

O for é uma estrutura de repetição parecida com while, porém baseado em um contador. Ele é composto por um bloco com três expressões que estabelecem uma contagem.
Veja o exemplo:

```php
<?php

for ($i = 1; $i <= 10; $i++) {
    echo $i . PHP_EOL; //PHP_EOL para quebrar linha.
}
