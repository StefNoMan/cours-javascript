# Cours JavaScript : Les fonctions

Les fonctions sont des ensembles d'instructions, des ensembles procéduraux permettant d'effectuer des altérations sur des valeurs ou des tâches.
Les fonctions sont l'un des fondements de la programmation avancée.

## définition

L'utilisation d'une fonction en JavaScript nécessite une définition de celle-ci. En tout cas, normalement.

```
function maPremiereFonction(value) {
	return value;
}
```

## argument

Les fonctions peuvent recevoir des arguments lors de leur déclaration.
Les arguments d'une fonction sont stockés dans un objet nomé **arguments**.
Par conséquent il est possible d'accéder au premier argunent d'une fonction de cette manière : **arguments[0]**. Nous pouvons ainsi connaître le nombre total d'arguments passés à une fonction grâce à l'instruction **arguments.length**.

```
var monArgumentPremier = 5;
var monSecondArgument = 'une phrase de quelques mots';

function maNouvelleFonction(maValeur) {
 var valeurFinale = maValeur = 10;
 return valeurFinale;
}

document.write( maNouvelleFontction(monArgumentPremier) );

```
Les variables définies dans une fonction, ont une portée limitée à la fonction.
une fonction **"enfant"** peut accéder à toutes les variables de la fonction **"parent"**.

## Anonymat

Une fonction en JavaScript peut-être anonyme (sans avoir de nom).

```
var monAddition = function(maVariable) { return maVariable + 10;}
var resultat = monAddition(5);
document.write(resultat);

```

## Récursion

Une fonction Javascript, même anonyme peut-être récurcive. Son comportement est semblable à une boucle.

```
var executante = function laFonction(laVariable) { return laVariable < 5 ? true : laVariable*laFonction(laVariable-1)  }

console.log( executante(6) );

```

Nous pouvons ainsi parcourir le DOM ([Mozilla Developper Network](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Fonctions)). 

```

function parcourirArbre(noeud) {
   if (noeud == null) //
      return;
   // faire quelque chose avec le noeud
   for (var i = 0; i < noeud.childNodes.length; i++) {
      parcourirArbre(noeud.childNodes[i]);
   }
}

```
## Imbrication

Il est possible d'imbriquer des fonctions.

```
function master(value) {
	function slave(valeur) {
		return value - valeur;
	}
	
	return slave;
}

fn_esclave = master(6):
valeurFinale = fn_esclave(4);

document.write(valeurFinale);

// seconde méthode

resultatAlternatif = master(6)(4);
dpcument.write(resultatAlternatif);

```
## la gestion d'événement

L'un des intérêts majeurs du JavaScript est sa capacité à intéragir avec le **DOM**. En effet la gestion des événements en JavaScript s'effectue par l'entremise de fonctions. Ces fonctions ne reçoivent q'un unique argument, l'événement. 
(Pour rappel le **DOM ou Document Object Model** est un standard de description d'interface d'un document XML ou HTML). 
Il est important de souligner que les événements sont procurés par le DOM et non par le JavaScript. Celui-ci ne fournit qu'une liaison.

```

window.onFocus = function() {
	document.body.style.backgroundColor = 'black';
}

```


## Gestion des exceptions

La gestion des exceptions au sein du Javascript se traduit de la manière suivante.  
Lorsque le code lance une exception, l'exécution en cours s'arrête et le pointeur remonte jusqu'à la fonction initiale de l'exécution et non sur la fonction ayant produit l'exception. Le code dépile.  
L'exception remonte donc **la pile** d'appel de fonctions en transmettant leur contexte.  
Il est possible d'intercepter ces exceptions, ainsi nous pouvons exécuter un certain nombre de procédures. Le programme est alors stoppé.

### Procédure

Pour lever une exception il suffit d'utiliser l'instruction **throw** suivit d'une expression à transmettre.  
Pour contrôler la gestion des exceptions, les instructions **try** et **catch** on été développées. **try** permet d'executer un ensemble d'instructions. Si une exception est levée, le bloc d'instructions **catch** prend la main.  
Il est possible d'ajouter à cet ensemble l'instruction **finally** qui offre la possibilité de terminer proprement le ou les processus engagés malgré la génération de l'exception.


```

// fonction d'enregistrement de la distance totale parcourue par vélo
function course(velo) {
	var kilometre = 0;


	// fonction de calcul de la distance parcourue
	function distance(velo) {
		kilometre++;
		if(kilometre === 10) {
			throw (new Error("la course est terminée."));
		}
	}	

	// fonction de démarrage
	function go(velo) {
		while(velo) {
		 	if(velo === null)
			throw "Pas de vélo !";
			console.log("je roule en "+velo);
			distance(velo);
		}
	}

	try {
		go(velo);
		return false;
	}
	catch(e) {
		console.log("la course est interrompue !");
		console.log(e.message);
		return true;
	}
	finally {
		console.log("la distance totale parcourue est de "+kilometre+" kms.");
	}
}

// lance la course
course('VTT');

``` 
