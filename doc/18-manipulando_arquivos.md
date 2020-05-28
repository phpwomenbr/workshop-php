# Manipulando arquivos e pastas

O PHP é uma linguagem de programação muito rica de recursos, e estes recursos ajudam muito no desenvolvimento de nossas aplicações com a linguagem.

Nesta aula vamos aprender as principais funções para manipular arquivos com o PHP.

## Criar Arquivos com PHP

A função `touch()` permite criar arquivos (caso ainda não existam), a utilização da função é muito simples, basta simplesmente passar um parâmetro com o nome do arquivo que deseja criar. Essa função devolve true em caso de sucesso ao criar o arquivo e false em caso de falha ao criar o arquivo.

Veja um exemplo, onde vamos criar um arquivo chamado teste.txt:
```php
touch('teste.txt');
```
> Extensões de arquivos não influência em nada, tanto faz para o PHP se a extensão é .txt .log ou .qualquercoisa.

## Verificando a existência de arquivos

`file_exist($nome_do_Arquivo)` é a função que verifica a existência de um arquivo. Geralmente é utilizada com o recurso como `if` e `while`. Ou seja a sintaxe seria:

```php
$nome_do_Arquivo = 'teste.txt';

if(file_exists($nome_do_Arquivo)) {
    echo "Existe" . PHP_EOL;
} else {
    echo 'Arquivo não encontrado' . PHP_EOL;
}
```
Se o arquivo estiver em um diretório, precisa especificar o caminho:
```php
file_exists('path/filename.txt')
```

Se tiver em um nível acima do diretório atual, precisa navegar até este diretório:
```php	
file_exists('../filename.txt')
```
## Renomear um Arquivo com PHP

Outra função muito interessante é a `rename()`, essa função permitir renomear o nome de um arquivo, nome ou sua extensão.

Neste exemplo, vamos pegar o arquivo `teste.txt` e renomear para `teste.pdf`.

```php
rename('teste.txt', 'teste.pdf'); // Arquivo teste.txt => teste.pdf
```
## Copiar Arquivos com PHP

A função `copy()` permite copiar um arquivo de um lugar para outro, seja para o mesmo nível de diretório ou qualquer outro diretório que você desejar copiar o arquivo.

Neste exemplo vamos copiar o arquivo test.log para test2.log, no final temos dois arquivos:
```php
copy('teste.pdf', 'copia_de_teste.pdf');
```

Se tiver que copiar o arquivo para um diretório existente, pode fazer desta forma:
```php
copy('teste.pdf', 'folder/copia_de_teste.pdf');
```
## Apagando arquivos

> **Obs**: Para apagar arquivos que estejam em um servidor é preciso primeiramente ter permissão de leitura e escrita nos arquivos.

`unlink($Nome_do_arquivo)` é a função que apaga arquivos. Esta função exclui o arquivo sem sem pedir confirmaćão,por isso, é recomendável fazer um script perguntando para o usuário se ele realmente deseja fazer a exclusão do arquivo.

Se utilizarmos a função `unlink()` dentro de uma condição, ela vai retornar verdadeiro caso o arquivo tenha sido excluido e falso caso o arquivo por algum motivo nao pode ser excluído.

```php
if(unlink($arquivo) == true) { //você pode substituir a variável $arquivo pelo nome do arquivo
    echo "Arquivo excluído";
}
```
## Lendo arquivos

O PHP é uma linguagem tem uma grande quantidade de funções que, as vezes, parecem fazer as mesmas coisas. Um bom exemplo disso são as funções que lêem arquivos.

Por exemplo, para ler um arquivo, você poderia usar as funções `file_get_contents`ou `fopen`, `readfile`. Apesar de serem parecidas, é necessário informar algumas variações entre as elas. 
Vamos ao primeiro exemplo:
### file_get_contents()
A função `file_get_contents` tem como finalidade ler todo o conteúdo de um arquivo para uma string, sendo possível, por exemplo, armazenar todo valor de um arquivo de texto em uma variável.

Exemplo:

```php
 $meu_Arquivo = file_get_contents('teste.pdf');
```
No exemplo acima, ao fazer essa chamada, você obteria toda o valor de `teste.pdf` em uma string e tratar conforme desejar.

### fopen()
Esta função abre um arquivo ou url. Ela recebe como parâmetro o nome do arquivo e o tipo de acesso (leitura, escrita, leitura e escrita).

```php
if (file_exists('teste.pdf')) {
    $arquivo_Aberto = fopen('teste.pdf', 'r+'); //Abre o arquivo para leitura
    $conteudo = fread($arquivo_Aberto, filesize('teste.pdf')); //Visualiza o conteúdo
    echo $conteudo . PHP_EOL;
}
```
> No exemplo acima foi utilizada a função `fread` para ler o conteúdo de um arquivo.

### readfile()
Ela lê e exibe todo o conteúdo de um arquivo. Diferentemente do `file_get_contents`, que retorna a string, a função readfile envia para a saída todo o conteúdo do arquivo. 

Exemplo:

```php
readfile('teste.pdf');
```
Então se você precisa trabalhar com os conteúdo do arquivo diretamente recomendável utilizar a função `file_get_contents`.

Se for o caso de apenas de exibir o conteúdo do arquivo, utilize `readfile`.

## Escrevendo em arquivos

Para escrever em um arquivo primeiramente também é preciso abrir o arquivo utilizando a função `fopen($arquivo, Tipo)` onde deverá ser passado dois parâmetros: o arquivo e a finalidade da abertura. As finalidades possíveis são:

- `r` Abre somente para leitura; coloca o ponteiro do arquivo no começo do arquivo.
- `r+` Abre para leitura e escrita; coloca o ponteiro do arquivo no começo do arquivo.
- `w` Abre somente para escrita; coloca o ponteiro do arquivo no começo do arquivo e reduz o comprimento do arquivo para zero. Se o arquivo não existir, tenta criá-lo.
- `w+` Abre para leitura e escrita; coloca o ponteiro do arquivo no começo do arquivo e reduz o comprimento do arquivo para zero. Se o arquivo não existir, tenta criá-lo.
- `a` Abre somente para escrita; coloca o ponteiro do arquivo no final do arquivo. Se o arquivo não existir, tenta criá-lo.
- `a+` Abre para leitura e escrita; coloca o ponteiro do arquivo no final do arquivo. Se o arquivo não existir, tenta criá-lo.
- `x` Cria e abre o arquivo somente para escrita; coloca o ponteiro no começo do arquivo. Se o arquivo já existir, a chamada a fopen() falhará, retornando FALSE e gerando um erro de nível E_WARNING. Se o arquivo não existir, tenta criá-lo. 
- `x+` Cria e abre o arquivo para leitura e escrita; coloca o ponteiro no começo do arquivo. Se o arquivo já existir, a chamada a fopen() falhará, retornando FALSE e gerando um erro de nível E_WARNING. Se o arquivo não existir, tenta criá-lo. 


Com o arquivo aberto é hora de fazer as modificações, utilizando o comando `fwrite($arquivo_aberto, $Informacao)`.

É importante chamar a função `fopen` em uma variável. Vejam um exemplo:

```php
if (file_exists($arquivo)) {
    $arquivo_aberto = fopen($arquivo, 'a+');
    $escrita = fwrite($arquivo_aberto, ‘Informacao’);
    fclose($arquivo_aberto);
}
```

[Voltar a página inicial](../README.md)