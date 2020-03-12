# Variáveis

Variáveis são espaços reservados na memória para armazenar dados. O conteúdo atribuído a uma variável, como o próprio nome diz, pode mudar sempre que necessário. Como a linguagem é fracamente tipada, não é necessário informar o tipo de dado na declaração.
As variáveis são representadas por um cifrão (`$`) seguido de um nome.

Exemplo: 
```php
$meu_nome = "Ana";
```
No exemplo acima estamos definindo uma variável chamada $meu_nome e ela está recebendo "Ana".

## Nomeação de variáveis 

É necessário ser feita respeitando algumas regras:

1. Não iniciar com números.
2. Não utilizar espaços em branco.
3. Não utilizar caracteres especiais, somente underline.
4. Pode ser declarada em minúsculo.
5. Pode ser usada em CamelCase.

Exemplo:

```php
$DataAniversario // uso de CamelCase
$dataAniversario // primeira minúscula e segunda maiúscula
$data_aniversario // uso de underline
```

> Como PHP é uma linguagem case sensitive, `$nomeum` é diferente de `$nomeUm`.

[Voltar a página inicial](../README.md)
