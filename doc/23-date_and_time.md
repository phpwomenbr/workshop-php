# Date and time: Manipulação de datas em PHP

Trabalhar com manipulação de datas é extremamente importante no desenvolvimento, manutenção de sistemas e para facilitar nosso dia a dia. O PHP possui várias funções para trabalhar com datas.  

As funções e classes relacionadas a data e hora não necessitam de instalação de extensão, pois são nativas do PHP.

Ao longo desse artigo vamos mostrar de forma conceitual e prática como utilizar estas funções e classes.

## Função [date()](php.net/date)
### Sintaxe
```php
  date ( string $format [, int $timestamp = time() ] ) : string
```
A função [`date()`](php.net/date) recebe dois parâmetros, o primeiro é uma string de formato e o segundo é o timestamp que é um valor inteiro e opcional, por isto na sintaxe ele vem entre colchetes.

Veja abaixo um exemplo de código para exibir o dia e a hora atual:

```php
// ANO-MÊS-DIA HORA:MINUTO:SEGUNDO
echo date('Y-m-d H:i:s') . PHP_EOL;
// Saída: 2020-12-03 20:56:30
``` 
Repare que cada letra passada como argumento tem um retorno diferente. Por exemplo, **H** formato de 24 horas de uma hora (00 a 23).

A seguir outras formas de formatação de saída da função [`date()`](php.net/date).

| Caracter | Descrição  |   
|---|---|
| d  | Dia do mês, 2 dígitos com zero à esquerda  |   
| D  |  Uma representação textual de um dia, três letras |  
| l ('L' minúsculo)  | A representação textual do dia da semana  |   
| z  | O dia do ano (iniciando em 0)  |   
| F  | Representação completa de um mês, como January ou March  |   
| m  | Representação numérica de um mês, com zero à esquerda  |   
| Y | Representação de ano completa, 4 dígitos  |   
| y  | Representação do ano com dois dígitos  |   


#### Dica
> Você pode utilizar a função [`date()`](php.net/date) para atualizar automaticamente o ano dos direitos autorais em seu site. Veja o exemplo:

```php
 &copy; 2015-<?php echo date('Y');?>
``` 
Conheça agora alguns caracteres comumente usados ​​para **horários**:

| Caracter | Descrição  |   
|---|---|
| H  | formato de 24 horas de uma hora (00 a 23)  |
| h  |  formato de 12 horas de uma hora com zeros à esquerda (01 a 12) |
|  i |  Minutos com zeros à esquerda (00 a 59) |
|  s  |  segundos com zeros à esquerda (00 a 59) |
|  a |  Ante meridiem minúsculo e Post meridiem (am ou pm) minúsculo |
|  A  | Ante meridiem minúsculo e Post meridiem (am ou pm) maiúsculo   |

Para exibir a hora atual no formato especificado, basta executar o código abaixo:

```php
echo 'Em Brasíla: ' . date('H:i:s') . ' horas...' . PHP_EOL;
// exibe o horário atual do servidor
```
### Trabalhando com fuso horário

Se ao executar o código acima a hora exibida não estiver correta, provavelmente é porque seu servidor está configurado para um fuso horário diferente do seu.

Se você precisa que o horário esteja correto de acordo com um local específico, terá que definir o fuso horário que deseja usar utilizando a função `date_default_timezone_set()`.

Veja um exemplo que define o fuso horário para 'America / New_York' e, em seguida, exibe a hora atual no formato especificado:

```php
date_default_timezone_set('America/New_York');
echo 'Hora atual em Nova York: ' . date('H:i:s a') . PHP_EOL;

date_default_timezone_set('America/Sao_Paulo');
echo 'Hora atual em São Paulo: ' . date('H:i:s a') . PHP_EOL;
``` 

**Obs:** É possível ver a lista de fusos horários suportados pelo DateTimeZone na própria [documetação](https://php.net/timezones) do PHP.

Outra forma de exibir a data e a hora é utilizando a função [`mktime()`](https://php.net/mktime). Ela recebe como parâmetros (hora, minuto, segundo, mês, dia, ano).Note que todos os argumentos são obrigatórios. Caso você não precise usar algum deles, basta preencher com `0`como vemos neste exemplo:
```php
$date = mktime(0, 0, 00, 12, 02, 2020);
echo 'Criado em: ' . date('d-m-Y ', $date) . PHP_EOL;
// Saída: Criado em: 02-12-2020 
```

## DateTime
Vimos até agora o uso de algumas funções `date`, mas é possível também utilizar orientação a objetos para fazer essas manipulações. Com a classe DateTime podemos instanciar e obter a data e hora atuais, por exemplo.

```php
// Pega o momento atual
$today = new DateTime();

// Exibe no formato desejado
echo $today->format('Y-m-d') . PHP_EOL;
``` 
Observe que neste exemplo, nenhum parâmetro foi passado para o construtor da classe DateTime, então o momento atual foi exibido.

## Adicionando datas
Você pode também adicionar datas de várias maneiras. Uma delas é especificando nos argumentos da classe DateTime. Ela recebe como parâmetro uma string de formato de data em inglês ou também uma string com uma data específica. Veja abaixo alguns exemplos:

```php
$agora = new DateTime('now'); // ou sem parâmetro
$amanha = new DateTime('tomorrow');
$proximo_ano = new DateTime('next year');
$data_aleatoria = new DateTime('2000-10-10');

echo $agora->format('Y-m-d') . PHP_EOL;
echo $amanha->format('Y-m-d') . PHP_EOL;
echo $proximo_ano->format('Y-m-d') . PHP_EOL;
echo $data_aleatoria->format('Y-m-d') . PHP_EOL;
```
> **OBS**: Em PHP variáveis podem ter acento no nome mas é bom evitar para não ter problemas com diferentes codificações de caracteres em diferentes sistemas operacionais.

### Adicionando datas - strtotime()

A função `strtotime()` recebe como parâmetro uma string de formato de data em inglês e tenta analisar esse formato. É como tentar transformar uma frase que possui possíveis informações de data em uma data real, como mostra o código a seguir:

```php
$data = strtotime('tomorrow');
echo date('Y-m-d', $data) . PHP_EOL;

$data = strtotime('next Friday');
echo date('Y-m-d', $data) . PHP_EOL;

$data = strtotime('+3 Months');
echo date('Y-m-d', $data) . PHP_EOL;
```
Agora imagine que você precise listar os próximos sábados a partir da data atual... No exemplo a seguir você consegue fazer isso facilmente utilizando a função `strtotime()`.

Veja:

```php
$data = strtotime('Sunday');
$data_final = strtotime('+4 weeks', $data);

while ($data < $data_final) {
  echo date('F d', $data) . PHP_EOL;
  $data = strtotime('+1 week', $data);
}
```
### Adicionando datas - DateTime::add
Outra forma de adicionar datas é utilizar o método `add` da classe `DateTime`. Com ele é possível acrescentar uma quantidade de dias, meses, anos, horas, minutos e segundos em um objeto `DateTime` passando para o método `add` a quantidade de períodos como no exemplo abaixo.

- P5D: Período de cinco dias
- P2M: Período de dois meses
- PT10S: Período de dez segundos
- P2YT20M: Período de dois anos e vinte minutos

Veja o como utilizar:

```php
$diff1Year = new DateInterval('P1Y');
$diff10Hours = new DateInterval('PT10H');

// Adiciona 1 ano em $date1
$date1 = new DateTime('2020-12-02 08:00:00');
$date1->add($diff1Year);
print_r($date1);

// Adiciona 10 horas em $date2
$date2 = new DateTime('2020-12-02 08:00:00');
$date2->add($diff10Hours);
print_r($date2);
```
Vimos até agora várias formas de adicionar datas e períodos usando funções e classes Date PHP. Mas, e se quiséssemos saber o intervalo entre duas datas? 

## Subtraindo datas
Da mesma maneira que conseguimos adicionar datas e horas, também podemos subtrair um determinado período sobre um objeto da classe `DateTime` utilizando a função `sub()`. Confira como é fácil.

```php
$date = new DateTime();
$date->sub(new DateInterval('P10D'));
// Retorna a data atual - 10 dias
print_r($date);
```

### Diferença de datas
Calcular a diferença de datas no PHP é muito simples de se fazer utilizando o método `diff()`.
Imagine que você queira descobrir quantos dias de vida tem uma pessoa...

```php
$data1 = new DateTime('1984-01-01'); 
$data2 = new DateTime(); 
$intervalo = $data1->diff($data2); 
echo $intervalo->format('Total de dias: %a') . PHP_EOL; 
echo $intervalo->format('Anos: %y %m meses e %d dias') . PHP_EOL;
```
Parabéns! Você acabou de descobrir que tem alguns muitos dias de vida.

## Concluindo

Manipular datas e hora no PHP é bem fácil! Não é cecessário utilizar nenhuma biblioteca externa para isso pois ele trás funções e classes nativas. Com elas você pode fazer diversas operações envolvendo comparação, adição, subtração de datas e muito mais.

Para conferir um pouco mais sobre o mundo de possibilidades de se trabalhar com datas e horas no PHP, consulte sua [documentação](https://php.net/datetime). Lá você verá uma lista completa de funções e poderá tranquilamente realizar diversas operações.