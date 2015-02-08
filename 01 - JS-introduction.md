#Cours JavaScript : Introduction

##Historique

Le langage JavaScript (JS) est un langage de programmation interprété, crée en 1995 par **Brendan Breich**.  
Le JS a la particularité d'être un langage orienté objet prototypé. En cela il diffère des langages usant des instances de classes. Les construteurs sont cependant présents, permettant ainsi de créer des propriétés telle que la création d'héritiers.  
En fin de compte le JavaScript est un abus de langage. Son véritable nom est ECMAscript (ES). JavaScript étant une version spécifique de l'ECMAscript,  dénomination qu'en avait fait Netscape lors de sa publication. L'ECMA (European Computer Manufacturers Association) étant l'association européenne pour la normalisation des systèmes d'information et de communication.

##Caractéristiques

Une des caractéristiques particulières du langage JavaScript est qu'il est dépendant du navigateur qui interprète son code. Chaque navigateur ayant son propre moteur d'exécution. Il est donc parfois délicat de conformer le code sur l'ensemble des navigateurs disponibles.  

Le langage étant peu typé, une attention particulière doit être portée lors de l'écriture du code afin d'éviter toute erreur de typage.   

Le JS est sensible à la casse. *helloWorld()* est donc différent de *Helloworld()* 

Globalement le langage JavaScript est très souple dans sa syntaxe ce qui le rend permissif. Il faut donc prêter une attention toute particulière dans la rédaction du code.


## Déclaration

Pour déclarer un code JS, nous pouvons opter pour trois solutions.  
Soit par le biais d'une insertion :
```
<script type="text/JavaScript"> ... </script>
```
Soit par l'ajout d'un fichier externe :
```
<script type="text/JavaScript" src="path/file.js"> </script>
```
Soit par l'utilisation des événements :
```
<a onclick="alert('Hello World !'); return false;">Click here</a> 
```

## Syntaxe

Si une chose est très spécifique au JavaScript, c'est bien sa synthaxe. Elle est déroutante voir abérante pour la plupart des programmeurs.
Voici un exemple :

```
var stringSize = 'hello world'.length;
```


## Vanilla ?

On appelle vanilla un code JavaScript ne faisant pas appel à une bibliothèque (Jquery, Mootool, etc.). Si vous écrivez un code en JavaScript pure, il est considéré comme "vanilla".