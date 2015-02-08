#Cours Javascript : Les opérateurs

## Les expressions

Une expression est un ensemble de codes qui nécéssite une résolution afin d'obtenir une valeur.

```
// exemple d'expression
var result = 3 + 4; // result a pour valeur 7
```
JavaScript définit plusieurs types d'expressions :  
- Les expressions logiques (true ou false)
- Les expressions arithmétiques (comprenant des nombres)
- Les expressions de chaînes de caractères
- Les expressions d'objets

## Les opérateurs

Les opérateurs sont des symboles qui permettent la manipulation de variables, de valeurs.
le Javascript utilise des opérateurs unaire, binaire ou ternaire. Leur nom définit le nombre d'opérandes nécessaires. Un opérateur binaire nécéssite deux opérandes.
```
var z = x + y;
```
### Opérateurs d'affectations
L'opérateur d'affectation affecte une valeur à une variable.

```
var x = 7;
```

Il est possible d'ajouter une opération arythémtique ou de comparaison à l'opérateur d'affectation.

```
x += y; // x = x + y;
```

### Opérateurs de comparaisons

L'opérateur de comparaison permet de comparer deux opérandes. Le résultat de cette comparaison est transmis sous la forme d'une valeur booléenne (true/false).

```
var x = 3;  
document.write(x == 4); // false  
```

Il est possible d'effectuer une comparaison **"stricte"** (===) des valeurs. Dans ce cas aucune conversion de type n'est éxecutée.

```
var y = '3';
document.write(y === 3); // false  
```

### Opérateurs binaires

Les opérateurs binaires effectuent des opérations sur des représentations binaires. En effet, les opérateurs binaires considèrent les opérandes comme des ensembles de 32 bits. 

Les opérateurs binaires sont au nombre de 7.  
L'opérateur **AND (&)** renvoie un 1 à chaque position binaire pour laquelle les bits des deux opérandes sont à 1.  

L'opérateur **OR (|)** renvoie un 1 à chaque position binaire pour laquelle au moins un des bits des deux opérandes est à 1.  

L'opérateur **XOR (^)** renvoie un 1 à chaque position binaire pour laquelle au plus un des bits des deux opérandes est à 1.  

L'opérateur **NOT (~)** Inverse les bits de l'opérande.  

L'opérateur de décalage binaire à gauche **<<** décale la représentation binaire de b bits sur la gauche et complète avec des zéros à droite.  

L'opérateur de décalage binaire à droite **>>** décale la représentation binaire de b bits sur la droite en ignorant les bits perdus.  

L'opérateur de décalage binaire à droite en complétant avec des zéros **>>>** décale la représentation binaire de b bits sur la droite en ignorant les bits perdus et ajoute des zéros sur la gauche.  


### Opérateurs logiques

Les opérateurs logiques permettent l'évaluation, de préférence binaires, des opérandes.
L'opérateur **AND (&&)** retroune **true** si les deux opérandes ont pour valeur **true**. 

```
var x = true;
var y = false;
document.write(x && y); // false
```

L'opérateur **OR (||)** retourne **true** si l'un des opérandes a pour valeur true. Si les deux opérandes ont pour valeur **false**, l'opérateur renvoie **false**.  
Dans le cas où l'ensemble des opérandes ne serait pas des booléens, l'opérateur renvoie le premier opérande si celui-ci peut-être converti à **true**.  

```
var x = true;
var y = false;
document.write(x || y); // true
```

L'opérateur logique négatif **(!)** renvoie la valeur **true** si son opérande peut être converti en la valeur **true**.

```
var x = false;
document.write(!x); // true
``` 

### Opérateurs arythmétiques

Ce type d'opérateurs permet d'effectuer des opérations sur les nombres.
Dans le cas d'une division par zéro, le résultat renvoyé est **Infinity**.

```
var x = 3;
var y = 4;
document.write(x + y); // 7
```
Il existe quatres opérateurs arythmétiques "spéciaux" :  
- L'incrément (++)
- Le Décrément (--)
- La négation unaire (-)
- Le modulo (%)

L'incrément ajoute 1 à la valeur de l'opérande.

```
var x = 1;
x++; // x == 2
```

Le décrément soutrait 1 à la valeur de l'opérande.

```
var x = 1;
x--; // x == 0
```

La Négation unaire altère la valeur en son opposé.

```
var x = 2;
-x; // x == -2
```

Le Modulo retourne le reste entier d'une division entre deux opérandes.

```
var x = 22;
var y = 4;
document.write(x % y); // 2
```

Des opérateurs arithmétiques courts sont disponibles tel que **+=**.

```
var x = 1;
x += 4;
document.write(x); // 5
```

### Opérateurs de chaînes de charactères

L'opérateur de **concatenation (+)** permet comme son nom l'indique la concaténation de plusieurs chaînes de charactères en une.

```
var string1 = "Hello";
var string2 = " ";
var string3 = "world";
var string4 = "!";

document.write(string1 + string2 + string3+ string2 + string4); // "Hello world !"
```

## Les opérateurs spéciaux

### opérateur ternaire
L'opérateur ternaire permet d'effectuer une condition logique sans passer par l'opérateur **if**.

```
var x = 34;
var y = 45;

(x ===y )? 'oui' : 'non'; // non
```

### opérateurs "directs"

#### delete
L'opérateur **delete** permet de supprimer un objet, un élément d'un objet, un tableau ou un élément d'un tableau.
L'opérateur retourne **true** en cas de succés, **false** en cas d'échec.
Il n'est possible de supprimer une variable que lorsque celle-ci est déclarée implicitement	. Elle est alors convertie en propriété avant d'étre supprimer.

```
monObjet = new Number();
var testVariable= 4;

delete monObjet; // true
delete testVariable; // false

```
#### in

L'opérateur **in** permet de savoir si une propriété est présente dans l'objet.
Elle retourne **true** le cas échéant.

```
maPropriété in monObjet;

```

#### new
L'opérateur **new** crée une instance d'objet (*Array, Boolean, Date, Function, Image, Number, Object, Option, RegExp, String*).

```
var monNouvelObjet = new Date(2015, 02, 09);
```

#### this

L'opérateur **this** offre la possibilité de faire directement référence à l'objet courant.

```
function switchEspece(primate) {
	this.espece = "Shimpanzé";
  console.log(this.espece);
}

var singe = new Object();
singe.espece = "Gorille";

switchEspece(singe);
```

#### instanceof

L'opérateur **instanceof** permet de savoir si un objet est du type spécifié.

```
var maChaine = new String("Hello world !");
var retour = maChaine instanceof String;
document.write(retour); // true

var maChaine = "Hello world !";
var retour = maChaine instanceof String;
document.write(retour); // false maChaine n'est pas un objet String.
```
#### typeof
L'opérateur **typeof** retourne le type de l'opérande sous la forme d'une chaîne de caractères.

```
maChaine = "Hello World !";
typeof(machaine); /// string
```
#### void
L'opérateur **void** offre la possibilité d'évaluer un expression et ce, sans retourner de valeur.

```
<!-- Le lien ne produit pas d'effet -->
<a href="javascript:void(0)">Cliquer ici</a>
```


