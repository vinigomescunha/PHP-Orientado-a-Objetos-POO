# PHP-Orientado-a-Objetos-POO-
PHP Orientado a Objetos (POO)

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
    public function meuMetodo(){
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
