#Cours Javascript : les variables

### Déclaration
Les variables en JS ne sont que peu typées. Il n'existe que **7 types** de données, **les nombres (integer or float), les chaînes de caractères (string), les booléens (bool), les tableaux (array) et les objets (object)**.

- integer / float
- string
- bool
- array
- object
  
Leur déclaration est facultative. par conséquent vous pouvez très bien déclarer une variable de cette manière :

```
screenText = "hello world !";
```

Il est fortement conseillé de déclarer les variables de manière standard :

```
var screenText = "Hello world !"
```

De plus, le langage Javascript est "loosely typed", le typage n'est donc pas systématique dans la déclaration

```
var myValue = 1234;
var myValue = "my string";
var my value [1,2,3,4];
```

### Portée
Une variable déclarée en dehors d'une quelconque fonction sera considérée comme **globale**. Il sera donc possible d'accéder à celle-ci n'importe où dans le code.
Si une variable est déclaré sans la préfixer du terme *var*, elle est normalement considérée **globale** également.  
Afin d'être précis, une variable globale est en définitif une propriété de l'objet global *window*. 

```
var aliment = 'nougat';
document.write(window.aliment); // 'nougat'
```

Si cette variable est déclarée au sein d'une fonction sa portée sera restreinte à la fonction. Elle sera considérée comme étant une variable **locale**.

```
var porte = "globale";

function displayScope() {
  var porte = "locale";
  document.write(porte); //locale
  document.write(window.porte); //globale
}

displayScope();
```

#### Valeurs spécifiques

Toute variable non initialisée, aura pour valeur **undefined**.  


#### Particularités
Le JavaScript utilise un typage dynamique. L'implication d'une chaîne de caractère et d'une valeur numérique dans une expression peut avoir des conséquences étonnantes.  
```
var a = 20 + " plus un"; // a contient "20 plus un"
var b = "20" - 1; // b contient 19
```

Si vous essayez d'accéder à une variable non déclarée. JavaScript vous renverra **referenceError**.


### Les littéraux
Est appelé litteral(aux) toute valeur ou ensemble de valeurs fixes qui est fourni de manière littérale au script JS.

```
var latteral = "ceci est une chaîne littérale";

var monObjetersonne = { prenom: 'Jean', nom: 'Fauque', age: 63 };
```

A parti de l'instant où vous affectez à une variable un ensemble de valeurs (0 à X), cet ensemble est considéré comme étant un *litteral*.


### Les tableaux

####Particularité du tableau

En javascript les difficultés sont nombreuses et les règles régissant la manipulation de données en font parti. Une variable ne peut contenir qu'une seule donnée. Ce qui rend certaines opérations plus complexes.  
Afin de remédier à ce problème, le JS offre une structuration des données permettant d'enregistrer plus d'une donnée dans une variable. Il sagit du **tableau**.

Comme pour les variables "standard", il existe plusieurs méthodes pour déclarer un tableau :

```
myTable = ["element_1","element_2","element_3"];

ou

var myTable = new array("element_1","element_2","element_3);
```

Pour créer un tableau associatif, il suffit d'affecter les données :

```
myTable["indexName"] = "dataValue"; 
```

###Les objets
En javaScript les objets contiennent une paire **propertyName : propertyValue**.

Il y a deux manières de créer des objets en JS.  
De façon *litéral* :

```
var myObject = {};
```

ou de façon *orienté objet* :

```
var myObject = ();
```

Vous pouvez créer une propriété d'objet a tout moment, lors de la déclaration de l'objet ou ultérieurement.

```
var myObject = {
	name: 'nameObject',
	ready: true
};
```

L'objet peut contenir une fonction comme propriété :

```
var myObject = {
	name: 'nameObject',
	ready: true,
	state: 'cool',
	getState: function() {
		return this.state;
	}
};

```
Pour accéder à la valeur d'une propriété, les méthodes ne manquent pas :

```
var myValue = myObject.name; // myValue contient "nameObject"
var myValue = myObject['name']; // myValue contient "nameObject"
```

Pour créer une nouvelle propriété, rien de plus simple :

```
var myValue = myObject.newProperty;
```

Ou directement : 

```
myObject.newProperty = "new value";
```

#### Référence

Les objets ne sont jamais copiés. Seule la référence est transmise d'un objet à un autre.

```
var myObject = {
	points: 10;
};

var cloneObject = myObject;

myObject.points = myObject.points / 2;

console.log(cloneObject.points); // it display 5;
```


 
