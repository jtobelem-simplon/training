# Exercices Python

## Etape 1 : Déclarons quelques variables

Dans un premier temps nous allons simplement utiliser l'interpréteur Python. Pour cela il suffit d'ouvrir un terminal et de taper la commande `python`. Vous devriez voir dans votre terminal en début de ligne `>>>`. Si c'est le cas, c'est le signe que vous pouvez écrire du Python.

A faire : déclarer des variables permettant de vous décrire avec :

- Votre prénom
- Votre nom
- Votre age
- Votre taille en cm
- Quelques lignes qui expliquent pourquoi vous rejoignez la formation

## Etape 2 : Utilisons les opérateurs

### Ex1
```python
mystery1 = 8 + 6
mystery2 = 8 - 6
```
Afficher avec **print** la variable qui est égale à 2.

### Ex2
```python
zebrasInZoo = 8
giraffesInZoo = 4
```
Créer une variable **animalsInZoo** qui contient le nombre total d'animaux dans le zoo. Afficher cette variable.

### Ex3
```python
prixInitial = 1500
tva = 0.20
```
Créer une variable **prixFinal** qui égale au prix initial plus le prix initial multiplié par la tva. Afficher cette variable.

### Ex4 : modulo et division entière
1. Remplir des boites de 6 œufs! Créer une variable **nbBoites** qui contient le nombre de boites pleines et une variable **nbOeufsRestant** pour le nombre d’œufs qui restent.

```python
nbOeufsParBoite = 6
nbOeufsTotal = 145

nbBoites
```

2. Dans un jeu de 32 cartes (7, 8, 9, ..., roi, as pour les couleurs pique, cœur, carreau, trèfle), on décide d'associer à chaque carte un numéro.
Le numéro de la carte est obtenu en multipliant le numéro de la couleur (0,1,2 ou 3) par le numéro de la figure (0,1,2,3 ... 7).

Exemple :
le 9 de pique a pour numéro = 2 + 0*8 = 2 (carte n°2 de la couleur 0)
la dame de cœur a pour numéro = 5 + 1*8 = 12 (carte n°5 de la couleur 1)

```python
numero_carte_mystere = 28
```

Créer une variable **numero_couleur** et **numero_figure** à retrouver à partir du numéro de la carte mystère. Vous pouvez vérifier que votre méthode fonctionne en retrouvant la couleur de la carte n°2 (9 de pique) ou de la carte n°13 (dame de cœur).

### Ex5 : inférieur, supérieur
```python
prixInitial = 1500
tva = 0.20

budget = 2000
```
Créer une variable **budgetSuffisant** qui indique si le budget est supérieur ou égal au prix initial plus le prix initial multiplié par la tva. Afficher cette variable.

### Ex6 : égalité
Pour éviter les doublons, on cherche à comparer des albums par rapport à leur durée totale et au nombre de chansons par album.

```python
songsA = 9
songsB = 9
albumLengthA = 41
albumLengthB = 53
```
Créer une variable **sameSongs** qui est vraie si les deux albums contiennent le même nombre de chansons.
Créer une variable **sameAlbumLength** qui est vraie si les deux albums ont la même longueur au total. Afficher ces variables.

### Ex7 : chaînes et nombres

```python
formateur = 'Jules'
langage = 'java'
version = 1.8
```

Créer une variable **description** du type :
Mon formateur <formateur> est fan de <langage>, surtout depuis la version <version>!!

Et afficher cette variable.

Pour aller plus loin, [défi sur hackerRank](https://www.hackerrank.com/challenges/python-arithmetic-operators/problem)

## Etape 3 : Conditionnons notre code

```python
periode = "a definir"
heure = 10
```

1. Créer une condition **if** qui affecte la valeur "matinée" à la variable **periode** si l'heure est inférieure à 10. Afficher ensuite un message du type : "bonne <periode>"
2. Ajouter un deuxième **if** qui affecte la valeur "après-midi" à la variable **periode** si l'heure est inférieure à 18. Tester avec heure = 10, cela devrait afficher "bonne après-midi" ...
3. Corriger en remplaçant le **if** précédent par **elif**. Tester avec heure = 10 et heure = 15.
4. Ajouter un **elif** si l'heure est inférieure à 0. Dans ce cas afficher "erreur de saisie" (remarque il aurait mieux valu arrêter le programme..)
5. Ajouter un **elif** si l'heure est supérieure à 24. Dans ce cas afficher "erreur de saisie" (remarque il aurait mieux valu arrêter le programme..)
6. Grouper les deux cas précédent en utilisant un **or**.
7. Dans tous les autres cas, affecter la valeur "soirée" à la variable **periode**. Tester avec heure = 8, heure = -5, heure = 12, heure = 18, heure = 23, heure = 35.

> Remarque : un bon programmeur (donc un peu flemmard), aura certainement préféré utiliser le **else** pour toutes les heures invalides plutôt que pour soirée, car cela permet de ne pas écrire la condition compliquée avec le **or**.

Pour aller plus loin, [défi sur hackerRank](https://www.hackerrank.com/challenges/py-if-else/problem)

## Etape 4 : Créons des fonctions

- Créer une fonction qui renvoie l'aire d'un triangle en prenant en paramètres base et hauteur.
- Créer une fonction qui renvoie le volume d'une sphère en prenant en paramètre son rayon.
- Créer une fonction qui renvoie un message donnant l'IMC d'une personne. Elle prendra en paramètre le prénom de la personne, son poids en kg et sa taille en cm.

Pour aller plus loin, [défi sur hackerRank](https://www.hackerrank.com/challenges/write-a-function/problem)


## Etape 5 : Listes

1. Créer une liste qui contient tous les prénoms du groupe.
2. Trier cette liste. Afficher tous les prénoms qui ont un indice impair.
3. Créer deux sous-listes groupe1 et groupe2 contenant chacun la moitié du groupe.

Pour aller plus loin, [défi sur hackerRank](https://www.hackerrank.com/challenges/python-lists/problem)


## Etape 6 : Boucles

1. Parcourir la liste précédente. Pour chaque prénom, afficher la longueur du prénom avec la fonction **len**.
2. Ajouter une variable **maximum** au début du programme qui vaut 0 au début. Pour chaque prénom, **si** la longueur du prénom est supérieur au maximum, remplacer maximum par cette valeur.
3. Afficher le prénom le plus long à la fin avec un message : "le prénom le plus long est <prénom>, il possède <nbLettres> lettres"

Pour aller plus loin, [défi sur hackerRank](https://www.hackerrank.com/challenges/python-loops/problem)



## Etape 7 : Entrées / Sorties

- Créer un programme qui lit tous les prenoms dans un fichier promo.txt (à créer avec un notepad) et les place dans une liste. Puis tire un élément aléatoire dans cette liste (en utilisant la fonction choice du module random) et écrit ce nom dans un nouveau fichier winner.txt
- Créer un programme qui va lire le fichier [films-2018.txt](../resource/films-2018.txt) et indiquer combien il y a de films sortis en 2018.

**Bonus**

- Créer un programme qui va lire le fichier [villes-france.txt](../resource/villes-france.txt) et indiquer combien de fois apparaît _TOULOUSE_ dans le fichier.
- Créer un programme qui va lire le fichier [villes-france.txt](../resource/villes-france.txt) et créer un nouveau fichier sans doublons (après modification, le nouveau fichier ne doit contenir qu'une seule fois le même nom de ville).
- Créer un programme qui va lire le fichier [villes-france.txt](../resource/villes-france.txt) et créer un nouveau fichier dans lequel chaque ligne donnera le nom d'une ville en affichant le nombre d’occurrence dans le fichier de départ. Ce fichier devra être trié par ordre alphabétique.
