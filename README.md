# Sujet SAÉ 1.02 :Comparaison d’approches algorithmiques

## 1. Compétences
![download](https://user-images.githubusercontent.com/86799118/215333519-d46e6207-0a76-4200-a28f-d9a7a5cff80f.png)

## 2. Préambule : Comparaison d’approches algorithmiques
Lorsque l’on cherche à résoudre un problème, il existe une infinité d’algorithmes qui fournissent une solution correcte. Dès lors, se pose la question de savoir si un algorithme est préférable par rapport à un autre. On doit donc se donner des critères qui nous permettront de comparer les algorithmes (et leur implémentation).

De nombreux critères sont envisageables pour évaluer les qualités d’un algorithme. Par exemple, dans un contexte où de nombreuses personnes contribuent à un même projet, le critère de lisibilité du code revêt une importance capitale. D’autres personnes, qui ne suivent pas forcément votre travail quotidiennement, doivent être capables de lire et de comprendre votre code rapidement. Autre exemple, avec le réchauffement climatique, la consommation d’énergie des systèmes informatiques devient une préoccupation majeure (ou tout du moins devrait l’être). Des travaux sont menés pour essayer de quantifier l’énergie consommée par des implémentations d’algorithmes sur une architecture donnée : cette consommation devient alors un critère de comparaison.

Le critère le plus évident (et sans doute le plus étudié) tourne autour de la performance des algorithmes. Lorsqu’un algorithme est implémenté et exécuté sur une machine, la performance est souvent vue comme le temps d’exécution de l’algorithme : moins l’algorithme met de temps à trouver la solution, plus il est performant.

## 3. Présentation de la SAÉ
### 3.1. Objectif : comparer des implémentations algorithmiques, développer le jeu de la vie, auto-évaluer sa solution
Dans cette SAÉ, nous allons vous proposer de choisir, en fonction de critères présentés ci-dessous, une implémentation du type MatriceEntier vue en TP et développée par des anciens étudiants. Toutes les solutions proposées passent les tests java du TP. Puis, à partir de cette implémentation, vous devrez développer un jeu de la vie et enfin évaluer la qualité de votre code en utilisant les mêmes critères que ceux utilisés pour choisir l’implémentation de MatriceEntier.

### 3.2. Evaluation des implémentations données :
Afin d’évaluer les implémentations fournies, nous vous proposons de noter les implémentations qui vous seront données selon plusieurs critères :
- Qualité de la javadoc produite,
- Qualité de codage : nommage des variables, lisibilité du code, messages d’exception explicites, réutilisation des sous-programmes…,
- Efficacité : quitter les boucles dès que le résultat est trouvé (rupture quand c’est possible), pas de boucle inutile, stocker le résultat d’une fonction dans une variable afin d’éviter plusieurs fois le même appel…

Pour chaque implémentation, noter les trois critères précédents (en insuffisant, correct, bien, parfait par exemple). Donner à chacun des trois critères précédents un coefficient en fonction de l’importance que vous lui portez. Choisir la meilleure implémentation de MatriceEntier compte tenu des critères et de leur poids.

### 3.3. Le jeu de la vie
Une application _Jeu de la vie_ est un automate cellulaire où des cellules naissent et meurent sur une grille selon les règles suivantes inventées en 1970 par John Horton Conway.
1. Une cellule morte possédant exactement trois voisines vivantes devient vivante.
2. Une cellule vivante possédant deux ou trois voisines vivantes reste vivante, sinon elle meurt.

#### 3.3.1. Conseil d’implémentation
Pour simplifier les calculs ultérieurs une grille de jeu de taille `n x n` sera implémentée par une matrice d’entiers de taille `(n + 2) x (n + 2)`.

Cette matrice contiendra :
- 0 pour une cellule morte (ou pas de cellule),
- 1 pour une cellule vivante.

Par exemple pour un JeuDeLaVie de taille `3 x 3`, on représentera chaque génération par une variable de type MatriceEntier de taille `(3+2) x (3+2))`. **Les bords de la grille de jeu sont des cellules initialisées à 0**. Ce choix permet de simplifier le calcul des voisins.

#### Déroulement du jeu

Exemple 1 :
a. Initialise la génération 0 ainsi :
```
0 0 0 0 0
0 1 0 0 0
0 0 1 0 0
0 0 0 1 0
0 0 0 0 0
```

b. Puis affiche l’état des 2 générations suivantes. Le résultat attendu est celui-ci :
```
Generation 0
0 0 0 0 0
0 1 0 0 0
0 0 1 0 0
0 0 0 1 0
0 0 0 0 0

Generation 1
0 0 0 0 0
0 0 0 0 0
0 0 1 0 0
0 0 0 0 0
0 0 0 0 0

Generation 2
0 0 0 0 0
0 0 0 0 0
0 0 0 0 0
0 0 0 0 0
0 0 0 0 0
```

Exemple 2 
a. initialise la génération 0 ainsi :
```
Generation 0
0 0 0 0 0 0 0
0 0 0 0 0 0 0
0 0 1 1 1 0 0
0 1 1 1 0 0 0
0 0 0 0 0 0 0
0 0 0 0 0 0 0
0 0 0 0 0 0 0
```

b. puis affiche l’état des 2 générations suivantes. Le résultat attendu est celui-ci :
```
Generation 0
0 0 0 0 0 0 0
0 0 0 0 0 0 0
0 0 1 1 1 0 0
0 1 1 1 0 0 0
0 0 0 0 0 0 0
0 0 0 0 0 0 0
0 0 0 0 0 0 0

Generation 1
0 0 0 0 0 0 0
0 0 0 1 0 0 0
0 1 0 0 1 0 0
0 1 0 0 1 0 0
0 0 1 0 0 0 0
0 0 0 0 0 0 0
0 0 0 0 0 0 0

Generation 2
0 0 0 0 0 0 0
0 0 0 0 0 0 0
0 0 1 1 1 0 0
0 1 1 1 0 0 0
0 0 0 0 0 0 0
0 0 0 0 0 0 0
0 0 0 0 0 0 0
```

### 3.4. Indications de développement
#### 3.4.1. Passer à la génération suivante
La matrice initiale est de type MatriceEntier, la génération suivante aussi. La structure de donnée "JeuDeLaVie" doit donc, entre autres, contenir deux générations de type MatriceEntier. Il semble aussi qu’un certain nombre de sous-programmes soient intéressants (ex : tester si une cellule d’une matrice est vivante, calculer combien de cellules voisines d’une cellule sont vivantes, savoir si la cellule sera vivante à la génération suivante, calculer la génération suivante …).

#### 3.4.2. Détecter la terminaison
On souhaite arrêter de produire une nouvelle génération soit quand on a 10 générations soit quand la nouvelle génération est identique à une génération précédente.

On souhaite disposer d’une opération `grilleConnue()` qui retourne VRAI si la grille de la génération courante a déja été rencontrée au cours d’une des générations précédentes.

1. Comment sauver l’historique des générations ?
Dans un tableau de chaînes de caractères où chaque chaîne représente la grille d’une génération.
2. Comment transformer une grille en chaine ?
3. Comment comparer 2 générations ?

#### 3.4.3. Ecrire dans un fichier html
1. Ecrire la grille du jeu au format HTML.
```
toHTML() : JeuDeLaVie -> String
```

Pour une grille contenant :
```
0 1 0
1 0 1
0 1 0
```

On souhaite obtenir le résultat suivant :

```html
<table border="1"><caption>Génération 0</caption>
<tr><td></td><td class='on'></td><td></td></tr>
<tr><td class='on'></td><td></td><td class='on'></td></tr>
<tr><td></td><td class='on'></td><td></td></tr>
</table>
```

1. Pour chaque matrice initiale testée, on souhaite placer toutes les versions HTML des générations des grilles du Jeu de La Vie dans un même fichier résultats. Ce fichier devra pouvoir être ouvert dans un navigateur.

Modifier vos différents programmes de test (un par matrice initiale afin que toutes les générations des grilles soient accumulées dans un fichier enregistré sur votre disque.

Votre main ne fera qu’appeler vos différents tests.

Le sous-programme qui va écrire dans le fichier pourra s’inspirer du code à trous suivant :

```java
static ... {
    String css = "<style>";
    css += "table";
    css += "{";
    css += "border-collapse:collapse;";
    css += "border: 1px solid black;";
    css += "width:100px;";
    css += "display: inline-table;";
    css += "}";
    css += "tr,td { border: 1px solid black; height:20px;}";
    css += ".on { background-color:grey; }";
    css += "</style>";

    String debutPage = "<html><head>" ;
    debutPage += "<title>TP: Jeu de la vie</title>" ;
    debutPage += "<meta http-equiv='Content-Type' content='application/xhtml+xml; charset=UTF-8' />" ;
    debutPage += css ;
    debutPage += "</head><body>" ;

    String finPage = "</body></html>" ;

    PrintStream out = new PrintStream(...);
    out.print(debutPage);
   //Ajouter vos affichages
    out.print(finPage);
    out.close();
  }
```

