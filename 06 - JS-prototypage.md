# Cours JavaScript : Le prototypage

## utilisation avancée des objets

Le langage JavaScript s'articule autour de l'objet, ensemble de propriétés déclaré par le couple **nom : valeur**. Lorsque une propriété est une fonction elle est nommé **méthode**. 
En JavaScript tout est objet. On entend par là le fait que l'ensmeble des types primitifs à l'exception de *null* et *undefined* est concidéré comme un objet.


### les propriétés
Les propriétés d'un objet peuvent se définir comme des variables liées à un objet. 

```
var velo = new Object();
velo.roue = 700;
velo.cadre = 54;
velo.type = 'course';

```

A la différence d'autres languages de programmation, les objets en JavaScript  
sont aussi concidérés comme des **tableaux associatifs**. Nous povons donc accéder à une propriété de la manière suivante : 

```
var velo = new Object;
velo["roue"] = 700;
velo["cadre"] = 54;
velo["type"] = "course";

console.log(velo.type);


```
Les propriétés des objets en JavaScript peuvent, à la différence des languages typés "Classe" ajouter ou supprimer une propriété à tout instant.


### le construteur

Le constructeur est le moyen le plus simple pour générer des types d'objets.
Pour ce faire nous définissons une fonction qui servira de constructeur d'objet.
Il suffira ensuite de faire appel à l'opérateur **new** pour créer un nouvel objet.
Dans le cas d'une fonction-constructeur, la convention de nommage stipule la mise en majuscule de la première lettre du nom de celle-ci.

```
function Cycle(roue, cadre, type) {
	this.roue = roue;
	this.cadre = cadre;
	this.type = type;
}

var monVelo = new Cycle(600,49,piste);

```

### les méthodes

#### Object.create
La méthode **Object.create** permet de créer un nouvel objet prédéfini sans faire appel à un constructeur.

```
var Cycle = {
	type : 'course',
	cadre : 54,
	roue : 700,
	plateau : 2,
	cassette : 11,
	nombreVitesses : function() {
		console.log(this.plateau * this.cassette);
	}
}

var monVelo = Object.create(Cycle);
monVelo.nombreVitesses();

var sonVelo = Object.create(Cycle);
sonVelo.plateau = 3;
sonVelo.nombreVitesses();

```

## prototypage

Un prototype peut-être défini comme l'objet dont héritera le nouvel objet créé.  
Cet objet nouvellement créé, hérite de l'ensemble des propriétés de l'objet dont il est issu.  
Un constructeur contient "**l'objet prototype**".

En JavaScript, si initialement on définit une propriété par son nom. On doit toujours faire référence à celle-ci par son nom et si, initialement, on la définit par son indice, on doit toujours faire référence à celle-ci par son indice.[Mozilla Developer Network](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Utiliser_les_objets). Cette règle ne s'applique pas aux objets provenant du language HTML.
Il est important de comprendre qu'un objet peut, à tout instant, définir de nouvelles propriétés.

### la propriété "prototype"

Il est possible de définir une nouvelle propriété à un objet en utilisant la propriété **prototype**. Nous pouvons ainsi ajouter une propriété à l'ensemble des objets définis par le prototype.

```
Cycle.prototype.geometrie = "normal";

monVelo.geometrie = "sloping";

```
Un objet "prototype" n'est qu'un modèle contenant des propriétés. Tout objet peut par conséquent devenir le prototype d'un autre objet qui le cas échéant héritera des propriétés du prototype.
Un objet ne peut être associé qu'à un seul prototype.

### l'héritage

Le Javascript ne permet pas l'utilisation de classes telles qu'elles sont définies dans d'autres languages comme le C ou le java. Cependant, le JavaScript possède un typage dynamique.  
Étant accés essentiellement sur l'objet, le prototypage et l'héritage qui en découle sont les éléments sur lesquels nous nous appuyons pour créer une programmation moderne en JavaScript.

Comme nous l'avons vu précédemment une fonction peut-être liée en à un objet en tant que propriété de celui-ci. Lors de l'héritage, les fonctions liées au prototype sont aussi disponibles pour le nouvel objet généré.

```
Cycle.prototype.reglages = function() {
	var resultats = "le cadre fait " + this.cadre + "cm. La cassette comporte " + this.cassete + " vittesses";  
	document.write(resultats);
}

var monVelo = new Cycle(600,49);
monVelo.reglages();

```

Il est possible de tester si un objet possède une propriété particulière. Pour ce faire, nous utilisons la méthode **hasOwnProperty**.
Cependant, la méthode ne peut parcourir le prototype de l'objet. Elle est d'ailleurs la seule méthode d'objet à ne pouvoir le faire. 
Voici un exemple concret de l'utilisation du prototypage et de l'héritage en JavaScript :

```
function Cycle() {
	this.cadre = 54;
	this.geometrie = "normal";
	this.type = "ville";
}

function Velo_course() {
	this.guidon = "course";
}

Velo_course.prototype = new Cycle();
var velo = new Velo_course;

console.log(velo.cadre);

```

Attention, lorsque une fonction est prototypée, le constructeur du prototype original est supprimé. Dans le cas ci-dessus, **Velo_course.constructor** fera référence à **Cycle** et non **Velo_course**. 
Si l'on souhaite ciblé le prototype de **Velo_course** il faut faire appel à la propriété **.__proto__.**. Dans ce cas, **Velo_course.constructor** fera bien référence à **Velo_course**.

```
Velo_course.prototype.__proto__ = new Cycle();

```

#### les méhodes Call et Apply

La méthode **Call** permet d'écrire une méthode et permettre à un objet d'en hériter directement.

```
function Cycle(cadre,geometrie,type) {
	this.cadre = cadre;
	this.geometrie = geometrie;
	this.type = type;
}

function Cross_Country(cadre, geometrie, type, jantes, vitesses) {
	Cycle.call(this, 54, "normal", "VTT");
	this.jantes = 26;
	this.vitesses = 22;
}

var velo = new Cross_Country;

console.log(velo.geometrie);

```
 
 Vous pouvez aussi chaîner le constructeur d'un objet.
 
 ```
 
 Cross_Country.prototype = Object.create(Cycle.prototype);
 var canyon = new Cross_Country(56, "normal", "VTT", 29, 11);
 
 console.log(canyon.type);
 
 ```

La méthode **Apply** est similaire à la méthode **Call** à l'exception que le type d'argument transmit est un tableau.

#### la méthde Bind

La méthode **Bind** crée une nouvelle fonction liée à une fonction. 
Le premier argument de la méthode **Bind** est **this** et il ne peut être modifié. Le second argument permet de transmettre des arguments à la fonction.


```
this.type = "course";

// etpae 1
var velo = { 
	type : "VTT", 
	consoleLog : function() {
		console.log(this.type);
	}   
}
velo.consoleLog();

// etape 2
var consoleLog = velo.consoleLog;
consoleLog();

// etape 3
var boundConsoleLog = consoleLog.bind(velo);
boundConsoleLog(); 

```


### le référent "This"

Le référent **this** par défaut fait référence à l'objet courant. 

```

  <a href="#" id="monLien">mon lien </a>

  <script type="text/javascript">
  var element = document.getElementById("monLien");
  element.onClick = function () {
    this.style.color="#FF0000";
    return false;
  }
  </script>

```

Nous pouvons utiliser la variable **self** pour conserver le référent **this**.

```

var velo = {
	cadre: 54,
	afficheCadre: function() {
		console.log(this.cadre);
	},
	viewFrame: function() {
		setTimeout( function() {
			console.log(this.cadre);
		}, 500);
	}
}

var cycle = {
	cadre: 54,
	afficheCadre: function() {
		console.log(this.cadre);
	},
	viewFrame: function() {
		var self = this;
		setTimeout( function() {
			console.log(self.cadre);
		}, 500);
	}
}

```
La méthode **.bind()** peut aussi permettre de concerver le référent **this**.

```
var cycle = {
	cadre: 54,
	afficheCadre: function() {
		console.log(this.cadre);
	},
	viewFrame: function() {
		setTimeout( ( function(){
    		console.log(this);
  		} ).bind(this), 100 );
	}
}

```


