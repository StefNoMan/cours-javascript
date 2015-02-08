#Cours Javascript : Les boucles

## les instructions de condition

### l'opérateur if

L'instruction **if** éxecute une instruction si une condition ou un ensemble de conditions est vérifié.

```
var validite = false;
var test = 'valide';

if(test === 'valide') {
	validite = true;
}
else if(test === 'invalide') {
	validite = false;
}
else {
	validite = false;
}

document.write(validite);

```

### l'opérateur switch
L'instruction **switch** évalue une expression en fonction des cas présentés et éxecute les instructions associées le cas échéant.

```
var choix = "vide";
var test = "second choix";

switch(test) {
	
	case "premier choix": 
		choix = "choix numéro 1"; break;
	
	case "second choix":
		choix = "choix numéro 2"; break;
		
	case "dernier choix":
		choix = "choix numéro 3"; break;
		
	default :
		choix = "choix par défaut"; break;
}

document.write(choix);

```

##Les boucles

Les boucles sont un groupe d'instructions qui permet de séquencer un ensemble de codes.

### la boucle for
Cette boucle éxecute un ensemble d'instructions tant que la condition initiale est respectée.

```
for(i = 0; i < 10; i++) {
	document.write("la valeur de i est : " + i + "<br>");
}

```

#### la boucle for in

Cette boucle parcourt dans un ordre arbitraire les propriétés d'un objet.

```
var monObjet = {propriete_1 : 1, propriete_2 : 2, propriete_3 : 3 };

for( var prop in monObjet) {
	document.write(prop + "<br>");
}

```
#### la boucle for each in

Cette boucle offre la même possibilité que la boucle **for in** mais au lieu d'itérer les noms des propriétés d'un objet, elle itére ses valeurs.

```
var monObjet = {propriete_1 : 1, propriete_2 : 2, propriete_3 : 3 };

for each ( var valeur in monObjet) {
	document.write(valeur + "<br>");
}

```


### les boucles while & do

#### la boucle while

Cette boucle exécute la séquence de codes tant que la condition est valide. 

```
var i = 0;

while(i < 5) {
	document.write("la valeur de i est : " + i + "<br>");
	i++;
}

```

#### la boucle do while

Cette boucle exécute la séquence d'instructions jusqu'à ce que la condition soit fausse. L'évaluation est effectué après exécution de la séquence.

```
var i = 0;
do {
   i += 1;
   document.write("la valeur de i est : " + i + "<br>");
} while (i < 5);

```
 



