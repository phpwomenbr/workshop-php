# Orientação a Objetos
Para muitos orientação a objetos é um conceito apavorante e com sintaxes complicadas. Nesta aula você aprenderá os conceitos que envolvem a programação orientada a objetos (POO) e conhecerá um mundo de possibilidades que a envolve.
A finalidade da POO é aproximar o mundo digital do mundo real e ela tráz inúmeras vantagens.

Imagine uma casa...

Certamente quem a construiu antes de começar fez um projeto de como seria esta casa, damos este nome de projeto de planta.

A partir de uma planta pode ser construída inúmeras casas, todas elas com o mesmo molde. Porém, cada casa pode ter uma cor diferente, uma porta diferente...

Em POO chamamos a planta da casa de Classe (modelo) e as casas geradas a partir deste modelo de objeto. Um novo objeto criado pode ser chamado de instância.

## Classes 
Uma classe é uma forma de definir um tipo de dado em uma linguagem orientada a objetos. Ela é formada por dados e comportamentos.
Com a classe definida, podem ser criados diversos objetos do tipo da classe criada. Ela funciona, então, como um modelo para a criação dos seus objetos.

## Objetos
Objetos são instâncias de classes, que determinam qual informação um objeto contém e como ele pode manipulá-la. É uma entidade capaz de reter um estado (informação) e que oferece uma série de informações (comportamento) para examinar ou para afetar este estado. É através deles que praticamente todo o processamento ocorre em sistemas implementados com linguagens de programação orientadas a objetos.

<kbd>
<img src="../images/exemplo_carro_1.jpg">
</kbd>

## Atributos e métodos
Para definir os dados são utilizados os atributos, e para definir o comportamento são utilizados métodos.

<kbd>
<img src="../images/exemplo_carro_2.jpg">
</kbd>

Atributos de uma classe também são conhecidos como propriedades e descrevem um intervalo de valores que as instâncias da classe podem apresentar.
Um atributo é uma variável que pertence a um objeto. Os dados de um objeto são armazenados nos seus atributos.
Informações sobre o objeto. Dados que posso armazenar.

Os métodos são procedimentos ou funções que realizam as ações próprias do objeto. Assim, os métodos são as ações que o objeto pode realizar. Tudo o que o objeto faz é através de seus métodos, pois é através dos seus métodos que um objeto se manifesta, através deles que o objeto interage com os outros objetos.
Sendo mais conhecidos como: Método Construtor, Métodos Get e Set, etc.

...
Class Casa(){
  // Atributos
  public $quartos;
  private $cor;
  
  // Métodos
  public function getCor(){
    return $this->cor;
  }
  public function setCor($cor){
    $this->cor = $cor;
  }
}
...

<kbd>
<img src="../images/exemplo_casa.jpg">
</kbd>


## Visibilidade

São distribuídas em três tipos, private (privado), public (publico) e protect (protegido):
- Privado: uma função local e um único bloco de código
- Público: visível para tudo uma função a ser chamada a qualquer momento
- Protegido: esse caso restringe o parâmetro fora da classe, mas ainda acessível às suas subclasses (herança)

...
Class Casa(){
  // Atributos
  public $quartos; // Não é necessários criar get e set para atributos publicos, pois ele podem ser acessados diretamente.
  private $cor;
  
  // Métodos
  // Método de get do atributo privado de Cor, somente atráves do método conseguiremos visualizar e setar um valor para o atributo.
  public function getCor(){
    return $this->cor;
  }
  public function setCor($cor){
    $this->cor = $cor;
    // Chamando um método privado na propria classe, ou seja, ao escolher uma cor também será setado o valor padrão de 3 quartos.
    $this->setQuarto();
  }
  
  //Método privados só podem ser utilizar na propria classe.
  private function setQuarto() {
    $this->quarto = 3;
  }
}
...


...
// Exemplo de como será criado e acesso o objeto
$casa = new Casa();

$casa->quartos = 3; // É possivel salvar um conteúdo de um atributo publico indo diretamento ao atributo.
echo $casa->quartos; // É possivel visualizar um atributo publico somente realizando a chamada dele.


$casa->cor = 'azul'; // Esse código não vai funcionar pois não é permitido acessar diretamente o atributo.
$casa->setCor('azul'); // No caso de atributo privado é necessário chamar o método set do atributo.

echo $casa->getCor(); // Mesma coisa para exibir o conteúdo de um atributo privado é necessário ter um método get desse atributo.
...

## Encapsulamento

O conceito do encapsulamento consiste em "esconder" os atributos da classe de quem for utilizá-la. Isso se deve por dois motivos principais.
Um é para que alguém que for usar a classe não a use de forma errada o outro motivo é de manter todo o código de uma determinada classe encapsulada dentro dela mesmo.

Encapsulamento vem de encapsular, que em programação orientada a objetos significa separar o programa em partes, o mais isolado possível. A idéia é tornar o software mais flexível, fácil de modificar e de criar novas implementações. O Encapsulamento serve para controlar o acesso aos atributos e métodos de uma classe. É uma forma eficiente de proteger os dados manipulados dentro da classe, além de determinar onde esta classe poderá ser manipulada

######## Faremos um exemplo na aula que será incluído aqui

## Associação de Classes

Uma associação define um relacionamento entre duas classes que permite que um objeto faça com que outro objeto realize uma ação em seu lugar.

Em termos gerais, a casualidade da ação é feita ao enviar uma mensagem ou invocar um método do objeto controlado.

######## Faremos um exemplo na aula que será incluído aqui

[Voltar a página inicial](../README.md)




