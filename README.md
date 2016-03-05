#PHP Orientado a Objetos (POO)


##Classes

Uma classe é um modelo de código para a gerar objetos, onde descreve as propriedades ou atributos, funções ou métodos. 


<?php

Class MinhaClasse {

    private $atributo1;
    protected $atributo2;
    public $atributo3;

    public function __construct($valor1, $valor2) { 
        $this->atributo1 = $valor1; 
        $this->atributo2 = $valor2;
    }

    public function MinhaFuncao ($valor1, $valor2) { 
        $retorno = $valor1 + $valor2;
        return $retorno;
    }
}

Class MinhaSegundaClasse {

    public $atributo = "";
    
    public function meuMetodo() {
        
        echo "this is my method";
        
    }
    
}

?>

##Objetos

Um objeto é criado a partir da definição de uma classe, portanto possui todos os atributos e métodos definidos em sua classe base e das classes às quais sua classe base herdou através da herança e por isso é dito que o objeto é do tipo da classe. Durante a execução de uma aplicação, somente objetos são utilizados, a classe é apenas um modelo para a construção destes objetos.

<?php

$Objeto = new MinhaSegundaClasse();

/* atributo público */

$Objeto->atributo = "meu atributo";

$Objeto->meuMetodo();

?>

##Herança

Conjunto de instâncias criadas a partir de outro conjunto de instâncias com características semelhantes, e os elementos deste subconjunto herdam todas as características do conjunto originalA palavra chave extends após o nome da classe filha na sua definição seguida pelo nome da superclasse

<?php

Class NomeSuperClasse {

}

Class NomeClasseFilha extends NomeSuperClasse {

  /* metodos e atributos da filha */
  
}

?>

##Classes Abstratas

Uma classe abstrata é sempre iniciada pela palavra chave abstract, não é possível criar objetos a partir da definição de uma classe abstrata. 
Se uma classe possui pelo menos um método abstrato também deve ser definida como abstrata.
Uma classe herdeira de uma classe abstrata deve implementar todos os métodos definidos como abstratos na classe base abstrata.
Um metodo abstrato indica que as classes filhas daquela classe onde se encontra o método, devem utilizá-lo, com o comportamento específico, métodos definidos como abstratos não podem ter implementação, é apenas uma definição do método

<?php

abstract class AbstractClassI18N {

    abstract public function getLanguage();
    
}

class BrazilianTags extends AbstractClassI18N {

    public function getLanguage() {
      return 'pt_br';
  }
  
}

?>

another example

<?php

abstract class Finances {
  
  abstract function salary() ;
  
}

class Teacher extends Finances {
  
    public function salary() {
        return $this->salary * 1.08;
    }
}

class Cook extends Finances {
  
    public function salary() {
        return $this->salary + 500;
    }
}

?>

Anothe example

<?php

abstract class Auto {

    protected $name;
    
    protected $fourwheels = 'Car';
    
    protected $twowheels = 'Motorcycle';
    

    public function getName() {
        
        return $this->name;
        
    }
    
    abstract public function runAuto();
    
    public function __construct($name) {
        
        $this->name = $name;
        
    }
}

class Motorcycle extends Auto {

    public function runAuto() {
        
        echo "Running a " . $this->twowheels . " -> " . $this->name;
        
    }
    
}

class Car extends Auto {

    public function runAuto() {
        
        echo "Running a " . $this->fourwheels . " -> " . $this->name;
        
    }
    
}

/*$auto = new Auto("Honda"); */

$car = new Car("BMW");
$motorcycle = new Motorcycle("Kawazaki");

$car->runAuto(); // Running a car -> BMW

$motorcycle->runAuto(); // Running a Motorcycle -> Kawazaki

?>

##Interfaces

interfaces de objetos permitem a criação de código que especifica quais métodos e variáveis uma classe deve implementar, sem ter que definir como estes métodos serão tratados.
Interfaces devem ser definidas usando a palavra chave "Interface" e todos os seus métodos devem ser declarados como public
Interfaces não podem ter conteúdo definido. 

Para implementar uma interface deve ser usado o operador implements e todos os métodos da interface devem ser implementados.

<?php

interface  MyInterface {

    public function set($name, $value); 
    public function get($name);
    public function display($variable);

}
?>

<?php

class MyClass implements  MyInterface { 

    private $attrs;
    
    public function set($name, $value) { 
        
        $this->attrs[$name] = $value;
        
    }
    
    public function get($name) {
        
        return $this->attrs[$name];
        
    }
    public function display ($variable) {

        foreach($this->attrs[$variable] as $k => $v) { 
            
            echo " key $k value $v";
            
        }
    }
}

?>


##Polimorfismo

No Polimorfismo podemos derivar classes de uma mesma superclasse e utilizar métodos iguais, porém com comportamentos diferentes. 

Um mesmo método se comporta de diferentes maneiras em diferentes classes.

Polimorfismo simplesmente significa reescrever um método da superclasse na subclasse

<?php

class SuperClass {
    public function display() {
        echo "I am a superclass";
    }
    
    function __construct() {
        $this->display();
    }
}


class Subclass extends SuperClass {
    public function display() {
        echo 'I am a subclass';
    }
    
    function __construct() {
        $this->display();
    }
}

$superclasse = new SuperClass;

$subclasse = new Subclass;

?>

##Encapsulamento

O encapsulamento é o ato de você provê uma proteção de acesso aos membros internos de um objeto.
A classe é responsável por seus atributos, e dessa forma podemos acessar esses atributos apenas com métodos da própria classe.
Os atributos/propriedades nunca devem ser acessadas de fora da classe, pois assim temos uma segurança maior sobre seus valores.
Para trabalharmos com o encapsulamento devemos entender como funciona a visibilidade dos atributos e métodos de um objeto.

Basicamente existem três tipos de visibilidade

**private**: Atributos ou métodos declarados como private só podem ser acessados dentro do escopo da própria classe em que foram declarados. Ou seja, não podemos acessar a partir de outras classes descendentes. 

**protected**: Atributos ou métodos declarados com protected somente podem ser acessadas dentro da própria classe ou a partir de classes descendentes (herdadas). 

**public**: Atributos ou métodos como public podem ser acessados de forma livre, a partir da própria classe, a partir de classes descendentes e a partir de programas que fazem uso dessa classe.

Se não declaramos visibilidade em membros (atributos e métodos) de uma classe automaticamente Será do tipo public.

<?php
class System {

    private $code;
    
    private $name;
    

    function SetName($name)  {

        if (is_string($name) && (strlen($name) > 0)) {
            $this->name = $name;
        }
    }

    function getName() {
        echo "The name is : {$this->name}";
        
    }
}
?>



##Padrões de Projeto

Em geral, os padrões de projeto são classificados em três tipos: padrões de criação, padrões estruturais e padrões comportamentais.

###Padrões de Criação

Os padrões de criação se preocupam com a instanciação de objetos. Esse padrão abstrai o processo de instanciação, ajudam a tornar o sistema independente de como objetos são criados, encapsulam conhecimento sobre quais classes concretas o sistema usa e esconde como instâncias dessas classes são criadas.

Os padrões "GoF"(Gang of Four) apresenta cinco padrões de criação: Singleton, Abstract Factory, Builder, Factory Method e Prototype.

####Padrão Singleton

Ess padrão é uma classe especial que gera uma e somente uma instância de objeto, o objetivo do Singleton é assegurar que uma classe tem uma única instância e estabelecer um ponto de acesso global para essa instância.
Este padrão é adequado para lidar com recursos que devem ser únicos em um sistema, como um controlador de um dispositivo ou um gerenciador. 
Como o padrão Singleton garante que só exista uma instância da classe, temos a certeza que todos os objetos que utilizam uma instância desta classe usam a mesma instância. A estrutura do padrão Singleton é bastante simples, composto por somente uma classe que instanciará  e caso ainda não exista, então ele solicitará a criação de um novo pelo construtor da classe, previne um possível stack overflow (estouro de pilha) nas aplicações.


<?php

class Automobile {

    private $vehicleMake;

    private $vehicleModel;

    public function __construct($make, $model) {
        
        $this->vehicleMake = $make;
        
        $this->vehicleModel = $model;
        
    }

    public function getMakeAndModel() {
        
        return $this->vehicleMake . ' ' . $this->vehicleModel;
        
    }
}

class AutomobileFactory {
    public static function create($make, $model) {
        
        return new Automobile($make, $model);
        
    }
}

$veyron = AutomobileFactory::create('Bugatti', 'Veyron');

print_r($veyron->getMakeAndModel()); // outputs "Bugatti Veyron"

?>



<?php 

class Conext { 

    public static $instance;
    
    private $info;
    
    function __construct() { 
    } 
    
    public static function getInstance() {
       if (!isset(self::$instance)) {
           
           self::$instance = new PDO("mysql:host={{$this->info['host']}};dbname={{$this->info['database']}}", 
            $this->info['user'], 
            $this->info['pass'], 
            array(PDO::MYSQL_ATTR_INIT_COMMAND => "SET NAMES utf8")); 
           
           self::$instance->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION); 
           
           self::$instance->setAttribute(PDO::ATTR_ORACLE_NULLS, PDO::NULL_EMPTY_STRING); 
           
       } 
       
       return self::$instance; 
       
   } 
   
}

?>

####Padrão Factory Method

Define uma interface para criar um objeto, mas deixa as subclasses decidirem qual classe será instanciada, permitindo a uma classe postergar a instanciação de subclasses. 
O padrão Factory Method aborda o problema de como criar instâncias de objetos quando seu código enfoca tipos abstratos.
Como a programação orientada a objetos enfatiza a utilização de classes abstratas, Factory Method ajuda a resolver este problema. Abaixo é possível observar a estrutura do padrão.

<?php
class Regional {

    private $type;
    
    function __construct( $type ) {
        $this->local = $type;
    }
    
}

abstract class EventFactory {

    abstract function newEvent($type);
    
}

class EventFactoryBrazil extends EventFactory {

    private $event;

    public function __construct() {

    }

    public function newEvent($type) { 
        
        if($type == "Regional") {
            
            $this->Evento = new Regional("my_location"); 
            return $this->Evento;
            
        }
        if($type == "Federal") {
            
            $this->Evento = new Regional("DF"); 
            return $this->Evento;
            
        }
        
    }
}
$x = new EventFactoryBrazil();
$x->newEvent("Federal");

?>
####Padrão Abstract Factory

Este padrão fornece uma interface para criar famílias de objetos relacionados ou dependentes sem especificar suas classes concretas. 
O padrão Abstract Factory aborda o problema de criar fábricas que produzam conjuntos relacionados de classes em grandes aplicações de forma que um sistema venha sofrer pouco impacto em mudanças.

<?php
abstract class Factory_Abstract_database {
  
    protected function __construct() {
        
    }

    abstract public function createinstance();
    
}

class Factory_Abstract_BD_Mysql extends Factory_Abstract_database {

    private $host;
    private $pass;
    private $user;
    private $database;
    
    public function __construct() {
        parent::__construct();
    }
    
    public function set($k, $v) {
        $this->$k = $v;
        return $this;
    } 

    public function createinstance() {
        $db = new  PDO("mysql:host={$this->host};dbname={$this->database}", $this->user, $this->pass);
        return $db;
    }
    
}

/* Redis connection */

class Factory_Abstract_BD_Redis  extends Factory_Abstract_database {
    
    public $host = "localhost"; 

    public function __construct() {

    }

    public function createInstance() {
        $redisClient = new Redis();
        
        try{
          $connection = $redisClient->connect( $this->host, 6379 );
          var_dump($connection);
      } catch( Exception $e ) {
          echo $e -> getMessage( );
      }
  }
}
$x = new Factory_Abstract_BD_Mysql();

$x->set("host", "localhost")->set("pass", "mypass")->set("database","test")->set("user","myuser");

$y = new Factory_Abstract_BD_redis(); 

?>

###Padrões Estruturais

Padrões estruturais tratam da forma como classes e objetos estão organizados para a formação de estruturas maiores, tem o objetivo de isolar do cliente como objetos estão associados.

Segundo a Gang of Four, os padrões estruturais podem ser divididos em sete, sendo eles: Adapter, Bridge, Composite, Decorator, Façade, Flyweight e Proxy.


####Padrão Composite

É uma forma de agregar e, depois, gerenciar grupos de objetos semelhantes, de modo que um objeto individual não pode ser distinto para um cliente a partir de uma coleção de objetos. O padrão Composite permite construir objetos complexos através de uma composição recursiva que define uma árvore de objetos, onde todos os objetos são acessados de maneira consistente e homogênea, já que todos possuem uma superclasse ou uma interface comum, os clientes podem tratar objetos individuais ou composições de objetos de maneira uniforme.

<?php

interface HtmlElement {

    public function __toString();
}

class H1 implements HtmlElement {

    private $_text;

    public function __construct($text) {
        $this->_text = $text;
    }

    public function __toString() {
        return "<h1>{$this->_text}</h1>";
    }
}

class P implements HtmlElement {

    private $_text;

    public function __construct($text) {
        $this->_text = $text;
    }

    public function __toString() {
        return "<p>{$this->_text}</p>";
    }
}

class Div implements HtmlElement {

    private $_children = array();

    public function addChild(HtmlElement $element) {
        $this->_children[] = $element;
    }

    public function __toString()
    {
        $html = "<div>\n";
        foreach ($this->_children as $child) {
            $html .= ' ' . $child ;
        }
        $html .= "</div>";
        return $html;
    }
}


$div = new Div();

$div->addChild(new H1('Title'));

$div->addChild(new P('Lorem ipsum...'));

$sub = new Div();

$sub->addChild(new P('Dolor sit amet...'));

$div->addChild($sub);

echo $div, "\n";

?>
####Padrão Decorator

O padrão Decorator possui uma estrutura semelhante à do padrão Composite, porém ajuda a modificar a funcionalidade de componentes concretos, ao invés de usar apenas herança para resolver o problema da variação de funcionalidade, o padrão Decorator usa composição e delegação. O padrão Decorator anexa responsabilidades adicionais a um objeto dinamicamente, fornecendo uma alternativa flexível de subclasse para estender a funcionalidade.
Permite a adição de comportamento a um objeto individual, tanto estaticamente ou dinamicamente, sem afetar o comportamento de outros objetos da mesma classe.

<?php

interface eMailBody {
public function display_body();
}

class eMail implements eMailBody {
public function display_body() {
        echo "This is the Email body.<br />";
    } 
}
 
abstract class emailBodyDecorator implements eMailBody {
     
    protected $emailBody;
     
    public function __construct(eMailBody $emailBody) {
    
        $this->emailBody = $emailBody;
    }

    abstract public function display_body();
     
}
class christmasEmailBody extends emailBodyDecorator {
     
    public function display_body() {
    
        echo 'Christmas';
        $this->emailBody->display_body();    
    }
}
 
class newYearEmailBody extends emailBodyDecorator {
 
    public function display_body() {
    
        echo 'New Year';
        $this->emailBody->display_body();
         
    }
 
}
/*Normal Email*/

$email = new eMail();

$email->display_body();

/*christmas*/

$email = new eMail();

$email = new christmasEmailBody($email);

$email->display_body();

/*new year*/ 

$email = new eMail();

$email = new newYearEmailBody($email);

$email->display_body();

?>
